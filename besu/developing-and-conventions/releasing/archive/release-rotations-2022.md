# Release Rotations 2022

A page to keep track of engineers [doing Besu releases](../../releasing/how-to-do-a-besu-release.md), as well as roughly how long the release process is taking.   
  

| Release Date | Cutoff Date | Release Version | Executor | Approver | Release Coordinator | Time Taken |
| --- | --- | --- | --- | --- | --- | --- |
| Jan 5 |     | 21.10.6 | Sally | Justin | Sally | 1h  |
| Jan 14 |     | 21.10.7 | Sally | Danno | Sally | 3h (cherry picking) |
| Jan 17 |     | 21.10.8 | Sally | Danno | Sally | 1h  |
| Jan 19 |     | 21.10.9 | Justin | Gary | Justin | 1.5hr |
| Jan 27 |     | 22.1.0-RC3 | Gary | Sally | Gary | 1.5hr |
| Jan 31 |     | 22.1.0-RC4 | Frank | Sally | Lucas | 1.5hr |
| Feb 17 |     | 22.1.0 |     |     | Lucas/Sally | 1.3hr so far (cherry picking)<br><br>1.5hrs updating canaries |
| Feb 25 |     | 22.1.1 (bi-weekly) | Danno |     |     |     |
| Mar 15 |     | 22.1.2 (bi-weekly) | Frank | Sally | Frank | 2.5h (1.5h spent fixing DCO) |
| Mar 31 |     | 22.1.3 (bi-weekly) | Stefan | Frank | Stefan | 1.75hr |
| Apr 13 |     | 22.1.4 (bi-weekly) | Lucas |     |     |     |
| April 4 |     | 22.4.0-RC1 | Justin | Karim | Justin | 1.5hr |
| Apr 28th |     | 22.4.0-RC2 | Gary |     |     |     |
| May 4th |     | 22.4.0 | Lucas | Sally | ?   | 1h release  <br>1.5h updating canaries |
| May 18th |     | 22.4.1 (bi-weekly)<br><br>(merge-ready ropsten) | Jason | Simon/Sally | Jason | 3hr (merging in flaky test fix, codeql oom, manifest docker step failed) |
| May 27th (early) |     | 22.4.2 (bi-weekly) | Gary |     |     |     |
| June 15 (might move up) |     | 22.4.3 (bi-weekly) | Justin | Stefan | Justin | 2hr, cherry picking a pr revert. |
| July 6 |     | 22.4.4 (patch) | Gary |     |     |     |
| July 6 |     | 22.7.0-RC1 | Sally |     |     |     |
| July 20 |     | 22.7.0-RC2 | Danno | Gary |     |     |
| July 27 |     | 22.7.0-RC3 | Gary | Justin, Meredith |     |     |
| Aug 3 |     | 22.7.0 | Danno | Gary |     |     |
| Aug 22 |     | 22.7.1 | Justin | Danno |     |     |
| Sept 7 |     | 22.7.2 | Gary | Danno |     | Merge Only Cherrypicks |
| Sep 21 |     | 22.7.3 | Gary | Justin |     | Mainline |
| Sep 26 |     | 22.7.4 | Justin | Fabio |     | off-cycle release |
| Oct 5 |     | 22.7.5 | Justin | Gary |     | off-cycle release |
|     |     | 22.7.6 | Gary | Justin |     |     |
| Oct 19 |     | 22.7.7 | Fabio | Justin/Gary |     |     |
| Oct 6 |     | 22.10.0-RC1 | Gary | Justin |     | Mainline |
| Oct 19 |     | 22.10.0-RC2 | Gary | Fabio |     |     |
| Nov 2 |     | 22.10.0 | Fabio | Karim |     |     |
| Nov 16 |     | ~22.10.1~  release not done because burn-in testing not satisfactory - following 22.10.x releases updated | Jason |     |     |     |
| Nov 30 |     | ~22.10.2~<br><br>22.10.1 | Gary | Jason |     |     |
| Dec 3 |     | 22.10.2 | Gary | Justin |     | Hotfix for SEGFAULTs on 22.10.1 |
| Dec 14 | Dec 9 PST | ~22.10.2~<br><br>22.10.3 | Jason |     |     |     |
| Dec 28 |     | 23.1.0-beta<br><br>22.10.4 | Gary |     |     | Beta - Not released as production ready. Will include EOF |
| Jan 11 |     | 23.1.0-RCx | Gary |     |     | start from main, cherry pick until done on 25th |

For further releases, see [Release Rotations 2023](../archive/release-rotations-2023.md)

## Volunteers

- Jiri
- Karim
- Danno
- Justin
- Gary
- Sally
- Stefan
- Lucas
- Jason