# Defect Prioritization Policy

What priority level is the bug?

# Deciding Priority

When deciding how to respond to a bug, consider the two variables of probability and severity and apply them to a risk matrix to determine the priority and corresponding action. These are based on a Mainnet use-case and Proof of Stake consensus with Besu.

## Probability

How likely are actual users to encounter the issue during their use of the product?

*A feature rarely used, with a high likelihood of failure may have a lower probability than a popular feature with a low likelihood of failure (due to a high number of customers affected).*

| **Frequent** | Will occur several times during common network conditions on Mainnet, across restarts, and be easily reproducible. |
| --- | --- |
| **Probable** | Likely to occur when engaging in a specific behavior or during common network conditions. |
| **Occasional** | Likely to occur during specific network conditions or with specific CLs/environments. |
| **Remote** | Unlikely but possible to occur in the lifetime of a validator. |
| **Improbable** | So unlikely, it can be assumed occurrence may not be experienced. |

## Severity

How bad is the problem when it does get encountered?

| **Catastrophic** | Data loss/corruption or slashing occurs or is very likely to occur for the user. Detrimental risk for a validator stack. Persists over a restart. |
| --- | --- |
| **Critical** | Requires a restart or user interaction for a node to continue operation for a validator to perform its duties. |
| **Moderate** | Some components are not working as intended, but the validator continues its duties, i.e. RPC accuracy. |
| **Marginal** | Non-critical components are functioning within limits, but with unintended behaviors or side-effects. |
| **Insignificant** | No significant threat posed and can be left unmediated. |

When judging the severity of the bug as insignificant, as the bug does not need addressing it automatically gets set as P5 (very low) priority.

## Risk Matrix

|  | Catastrophic | Critical | Moderate | Marginal |
| --- | --- | --- | --- | --- |
| Frequent | Very High | High | High | Medium |
| Probable | High | High | Medium | Medium |
| Occasional | High | Medium | Medium | Low |
| Remote | Medium | Medium | Low | Low |
| Infrequent | Medium | Low | Low | Very Low |

## Priority Levels

| **Priority** | **Risk** | Policy (recommended actions) |
| --- | --- | --- |
| P1 | Very High | Picked up immediately, taking priority over that work. It may very well require the effort of more than one team member, possibly including the whole team. Target may require hot-fix release out of cycle.Alternatively notify security-besu@lists.hyperledger.org to invoke handling of the issues under HLF security policy. |
| P2 | High | Added immediately to the top of the backlog and resolution starts as soon as logically possible. Ideally, it should be resolved before the next release, or with a hot-fix depending on testing and burn-in. Team decides who can best address the issue. |
| P3 | Medium | Added as a priority for the next release, at the discretion of the product owner. |
| P4 | Low | Documented. Discussed in the next planning meeting at the discretion of the product owner.Candidate for a Good First Issue for the community. |
| P5 | Very Low | Documented in list of known issues. Revisited only if severity or likelihood increases or at the discretion of the product owner.Candidate for a Good First Issue for the community. |

