_Last updated: 2026-10-26_

## Summary

A default Besu node is not affected and needs no action. Default means a bundled network (for example mainnet), no TLS options and no HTTPS URLs in its configuration. Besu is affected only when the operator turns on one of the features listed below.

On 2026-10-17, the private keys of eight eMudhra (emSign) intermediate certificate authorities were shown to be recoverable from their public certificates. They were revoked on 2026-10-18, and browsers, operating systems and Go have since blocked them.

Java does not check revocation by default, so Java runtimes need their own fix. Anyone holding one of these keys can create a certificate that Java accepts as genuine. This includes the Eclipse Temurin runtime in the Besu Docker images.

OpenJDK shipped two fixes: on 2026-10-20 it blocked the compromised intermediates and their Sectigo cross-signs (`CVE-2026-91403`), and on 2026-10-23 it removed four eMudhra and Sectigo roots (`CVE-2026-114820`). 

On a runtime with neither fix, there are two ways Besu can be exposed:

- **Inbound, with no interception needed.** If JSON-RPC TLS client authentication is set to accept CA-signed clients, an attacker can create a client certificate and connect directly. This is the most serious case.
- **Outbound, if an attacker can intercept traffic.** When Besu connects to an `https://` or `wss://` endpoint, an attacker who can intercept the traffic can impersonate that endpoint.

## Am I affected?

How exposed you are depends on how the node is configured and where it runs. Check each row:

| If you use… | Why it matters | Affected? |
| --- | --- | --- |
| `--rpc-http-tls-ca-clients-enabled` | Besu accepts any client certificate that chains to a root in Java's default trust store, as well as clients in the known-clients file. The Engine API port uses the same `--rpc-http-tls-*` settings, so the same applies there. | **Yes, high risk.** No interception needed. |
| `--rpc-http-tls-known-clients-file` or `--rpc-http-tls-truststore-file` only, without the CA flag | Only clients you listed, or CAs in your own trust store, are accepted | No, unless your trust store is a copy of the JDK `cacerts` |
| `--rpc-ws-ssl-client-auth-enabled` or `--graphql-mtls-enabled` | Always uses the trust store or certificate file you supply | No, unless that file is a copy of the JDK `cacerts` |
| `--era1-import-prepipeline-enabled` (off by default) | ERA1 history is downloaded over HTTPS. The default `--era1-data-uri` is `https://mainnet.era1.nimbus.team/`. | Yes, if an attacker can intercept traffic |
| `--bootnodes` set to an `https://` URL, including `bootnodes` in a `--config-file` or the `BESU_BOOTNODES` environment variable | The bootnode list is downloaded over HTTPS when Besu starts. Without this option, Besu uses the bootnodes bundled with the network and downloads nothing. | Yes, if an attacker can intercept traffic |
| `--ethstats` | Connects over `wss://` and trusts Java's default roots unless `--ethstats-cacert-file` is set | Yes, if an attacker can intercept traffic and no CA file is set |
| `--metrics-protocol=opentelemetry` with an `https://` endpoint in `OTEL_EXPORTER_OTLP_*` | The OpenTelemetry exporter trusts Java's default roots | Yes, if an attacker can intercept traffic and `OTEL_EXPORTER_OTLP_CERTIFICATE` is not set |
| Docker image with the Pyroscope agent enabled and an `https://` server address | The agent trusts Java's default roots | Yes, if an attacker can intercept traffic |
| Plugins that make HTTPS calls, such as a remote `--security-module` | Plugins inherit Java's default trust store unless they configure their own | Check with the plugin's maintainer |

If your bootnode URL uses `http://`, it was already open to tampering before this incident. Download the list and pass a local path to `--bootnodes`.

These parts of Besu are **not affected**:

- **Peer-to-peer networking:** RLPx, discv4 and discv5 do not use certificate authorities.
- **DNS discovery (`--discovery-dns-url`):** it uses plain DNS, and each `enrtree://` list is checked against the public key in its URL.
- **Engine API with JWT authentication:** this is the default. JWT is a shared secret and does not involve certificate authorities.
- **Prometheus metrics (`--metrics-enabled`, the default protocol):** Prometheus pulls from a plain HTTP endpoint on the node. No TLS is involved.
- **Metrics push gateway (`--metrics-push-enabled`):** it pushes over plain HTTP only.
- **Genesis and network configuration:** these are local files or bundled with Besu.
- **UPnP NAT:** this stays on the local network and does not use HTTPS.

### How your environment changes the risk

- **Where the RPC port can be reached.** The client authentication issue needs only network access to the RPC or Engine port. A port exposed to the internet, a shared VPC or a Kubernetes cluster without network policies is open to anyone who can reach it. A port bound to `localhost` or behind a firewall allow-list greatly reduces the risk.
- **Which APIs are enabled.** If client authentication is the only control, an attacker gets every API in `--rpc-http-api`, including ADMIN, DEBUG and TXPOOL if they are enabled. Adding `--rpc-http-authentication-enabled` means they also need valid credentials or a JWT. The Engine API still needs its JWT unless `--engine-jwt-disabled` is set.
- **Network path for outbound connections.** Intercepting traffic needs a position on the path, such as shared hosting, a cloud provider, a compromised router or a hostile Wi-Fi network. A node in a controlled data centre is less exposed than one on shared infrastructure.
- **How Java was installed.**
  - **Docker image:** it ships Eclipse Temurin. Its trust store has the emSign ECC Root CA - G3 but no AAA Certificate Services root.
  - **Oracle and OpenJDK builds:** they include both roots.
  - **Ubuntu and Debian packages:** Java uses `/etc/ssl/certs/java/cacerts`, which takes extra steps to update (see CVE guidance).
  - **RHEL, Fedora and others:** Java uses the operating system's certificate store.

## What an attacker could do

| Endpoint | Worst case |
| --- | --- |
| JSON-RPC or Engine API with `--rpc-http-tls-ca-clients-enabled` | Pass client authentication and call any enabled RPC method without further credentials. ADMIN, DEBUG and TXPOOL let an attacker change peers, read node internals or flood the transaction pool. |
| ERA1 download | Serve forged or missing history. Blocks still go through full import and must link back to genesis, so the likely result is a stalled or wasted sync. Besu does not check ERA1 accumulators. |
| Bootnode URL | Replace the bootnode list with attacker-run peers to try to isolate the node from the honest network when it starts. |
| Ethstats | Capture the ethstats secret and the node's reported stats. |
| OpenTelemetry or Pyroscope | Read metrics, traces or profiling data. |

No exploitation has been reported.

## How to reduce exposure in Besu

### JSON-RPC client authentication: remove the CA flag

Remove `--rpc-http-tls-ca-clients-enabled`. List trusted clients with `--rpc-http-tls-known-clients-file`, or set `--rpc-http-tls-truststore-file` to a trust store holding only your own CA. This fixes the issue, regardless of the roots Java trusts. If you must keep the flag, see How to fix your Java runtime.

### Pin certificates where Besu supports it

These settings protect a connection whatever roots Java trusts:

- **Ethstats:** set `--ethstats-cacert-file` to your ethstats server's CA. Also give the server address an explicit `wss://` scheme. Without a scheme, Besu falls back to unencrypted `ws://` if the TLS connection fails.
- **OpenTelemetry:** set `OTEL_EXPORTER_OTLP_CERTIFICATE` to your collector's CA.
- **ERA1 and bootnodes:** download the files yourself and pass local paths to `--era1-data-uri` and `--bootnodes`.

## How to fix your Java runtime

We recommend you follow the official CVE guidance for checking if you are vulnerable and fixing:
- OpenJDK guidance - https://openjdk.org/emudhra
    - [OpenJDK vulnerability advisory, 2026-10-21](https://openjdk.org/groups/vulnerability/advisories/2026-10-21): CVE-2026-91403
    - [OpenJDK vulnerability advisory, 2026-10-24](https://openjdk.org/groups/vulnerability/advisories/2026-10-24): CVE-2026-114820
- Oracle guidance - https://ops.java/emudhra
    - [Oracle Security Alert Advisory: CVE-2026-91403](https://www.oracle.com/security-alerts/alert-cve-2026-91403.html)
    - [Oracle Security Alert Advisory: CVE-2026-114820](https://www.oracle.com/security-alerts/alert-cve-2026-114820.html)

## What the Besu team is doing

The Besu team is actively monitoring the situation and can provide further guidance on Discord.

For Docker users, look out for a future release which will contain a patched version of the Eclipse Temurin runtime we use in the Dockerfile.

## References

- [OpenJDK: guidance on the eMudhra certificates](https://openjdk.org/emudhra)
- [OpenJDK vulnerability advisory, 2026-10-21](https://openjdk.org/groups/vulnerability/advisories/2026-10-21): CVE-2026-91403
- [OpenJDK vulnerability advisory, 2026-10-24](https://openjdk.org/groups/vulnerability/advisories/2026-10-24): CVE-2026-114820
- [OpenJDK CheckCerts.java diagnostic](https://cr.openjdk.org/~mr/CheckCerts.java)
- [Oracle: guidance on the eMudhra certificates](https://ops.java/emudhra)
- [Oracle Security Alert Advisory: CVE-2026-91403](https://www.oracle.com/security-alerts/alert-cve-2026-91403.html)
- [Oracle Security Alert Advisory: CVE-2026-114820](https://www.oracle.com/security-alerts/alert-cve-2026-114820.html)
- [Mozilla bug 2083449](https://bugzilla.mozilla.org/show_bug.cgi?id=2083449): the incident record
- [eMudhra statement on the incident](https://emudhra.com/en/post/certificate-security-incident)
- [BellSoft: distrusting the eMudhra intermediates in Java](https://bell-sw.com/blog/distrusting-compromised-emudhra-intermediates-in-java/): test results for Temurin and other Java runtimes
- [Eclipse Temurin trust store update](https://github.com/adoptium/temurin-build/pull/4587)
- [Debian bug 1069251](https://bugs.debian.org/1069251): why `ca-certificates-java` updates don't refresh Java's trust store
