# 2022-05-30 Phishing PRs

May 30 2022: several suspicious (closed) PRs were noticed (on besu and other non-hyperledger repos). Several attempts to add a command to our Circle CI jobs that would retrieve contents of environment variables and send to a remote server.

User was reported to github (and has been removed)

Issue reported to Circle CI and they reported back:

- secrets were not exposed
- Recommend disabling this CI setting: **Pass secrets to builds from forked pull requests**
- Recommend rotating credentials

Unfortunately, disabling the "pass secrets to forked PRs" means that Sonar can't run on PRs

- plan is to temporarily disable this while we figure out a solution