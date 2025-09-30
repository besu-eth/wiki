# [ACCEPTED] DEBUG Log Improvement Proposal

# Problem

\--logging=DEBUG level is too spammy for end users and either we have to use the ADMIN RPC endpoint to target packages/classes or get them to post full logs which is a barrier and error prone.

# Goal

End users can enable --logging=DEBUG and have a chance at spotting an issue or pasting relevant snippets into support channels.

##   
DEBUG Principles

-  Aimed at both end users and developers
-  Should lead to resolution of common problems, whilst not spamming
-  Should not contain logs that take up more than one terminal screen, e.g. raw data, including RLP

## DEBUG Guidelines

- Should not include peer discovery
- Should not include txpool management
- Could include some peering to debug peering issues
- Could include some high level syncing
- Could include API requests, including potentially truncated data, but not full RLP

##   
TRACE principles

- Aimed at developers
- Expectation is everything is there and it's spammy
- Only useful when targetting certain packages/classes

  

# Actions (if no objections)

- Submit PR(s) to move logs from DEBUG → TRACE and any other tidy up to follow the proposal
- Update existing documentation, e.g [Coding Conventions](../../developing-and-conventions/coding-conventions.md) and [Logging](../../developing-and-conventions/logging.md)