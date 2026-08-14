# Security Policy

This page describes how to report a security issue in Besu, how we handle it, and how we disclose it.

## Reporting a security issue

If you think you have found a security vulnerability in Besu, please report it privately. Do not open a public GitHub issue.

**Reporting channels:**

1. **Email:** [`security-besu@lists.hyperledger.org`](mailto:security-besu@lists.hyperledger.org) — visible only to Besu maintainers and LF Decentralized Trust staff. Use this for reporting issues directly to Besu.
2. **[Ethereum Bug Bounty Program](https://ethereum.org/bug-bounty/)** — visible to EF security team, who pass it onto relevant EL/CL client teams. Use this for issues that affect multiple clients on Ethereum mainnet.
3. **Email:** [`security@hyperledger.org`](mailto:security@hyperledger.org) — broader LF Decentralized Trust security team. May be viewed by maintainers outside Besu. Use this for issues that affect LFDT projects other than Besu.

In your report, please include:
- A description of the vulnerability, including as much information as possible about the impact and severity
- Reproduction steps
- The affected Besu version(s)
- Whether you believe the issue is being actively exploited

## How we handle reports

1. **Acknowledgement** — we aim to acknowledge receipt within 5 business days.
2. **Triage** — the security list assesses severity using the [Defect Prioritization Guide](Defect-Prioritization-Guide). We will keep you informed of our assessment.
3. **Fix development** — fixes are developed privately. For issues that affect other Ethereum clients or require ecosystem-wide coordination, we follow the [Ethereum security disclosure
   process](https://github.com/ethereum/consensus-specs/blob/dev/SECURITY.md) and work with relevant teams before releasing.
4. **Release** — the fix ships in a Besu release. We will notify you before the release if possible.
5. **Disclosure** — after a fixed version has been available for a reasonable period, we publish a GitHub Security Advisory (GHSA) with the vulnerability details, affected versions, fix version, and reporter credit (with your consent).

We do not publish vulnerability details before a fix is available in a released version.

## Disclosure timeline

We aim to disclose publicly, within a short window, after a fixed release is available. The window may be longer for issues that require broad ecosystem coordination or that affect consensus. For critical issues, we may proactively notify
operators through known channels before or alongside the GHSA.

## Security advisories

We publish [GitHub Security Advisories (GHSAs)](https://github.com/besu-eth/besu/security/advisories) for security-relevant fixes. From 2026 onward, we use GHSAs as our standard disclosure record. Older security fixes may not have
corresponding advisories.

## Security list members

The members are:

| Name | Affiliation |
| --- | --- |
| Gary Schulte | Consensys |
| Jason Frame | Consensys |
| Fabio Di Fabio | Consensys |
| Sally MacFarlane | Consensys |
| Karim Taam | Consensys |
| Simon Dudley | Consensys |
| Justin Florentine | Consensys |
| Ry Jones | Linux Foundation |
| Hart Montgomery | Linux Foundation |
