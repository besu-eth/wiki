# Grants

# Context 

Besu is a unique client in that it qualifies for many Mainnet related grants but has an open-source contributor base. This can make splitting grant rewards difficult and inequitable. This document provides a process for applying for grants and determining / splitting rewards from any received grants. This includes compensation for engineers or their parent organizations (if any). 

# Related Docs

[CIP Splitter Contract](https://app.0xsplits.xyz/accounts/0x4008Ed96594b645f057c9998a2924545fAbB6545/)

[Besu Contributor Call where grants were discussed with participants](https://lf-hyperledger.atlassian.net/wiki/display/BESU/2023-01-31+Contributor+Call+-+AMEA+Reschedule)

# Process

Based on the notes from the [Jan 31 2023 contributor call](https://lf-hyperledger.atlassian.net/wiki/display/BESU/2023-01-31+Contributor+Call+-+AMEA+Reschedule) (participants Danno, Web3Labs, CSI Besu team), the following process was suggested around grants: 

- Work-share decided amongst contributors that are interested in pursuing a grant:
- I.e. CSI pursues this grant and is the only group working on it, taking full split. 
- I.e. CSI, Swirld Labs, ETC Co-Op decide to pursue a grant as the Besu project, then split the grant based on agreed-upon work share. 
- Make use of transparent splitter contracts to divide the funds, using [0xSplits](https://www.0xsplits.xyz/).
- Agreements in writing shared amongst contributors in advance. 
- Arbitration by grantor as needed, since it is their funding. This is a fail-over mode. 
- Transparency is key - discussions to be done on Discord or on calls recorded/with shared notes

  

This would allow individual groups to pursue grant opportunities as they see fit. They can retain funds unless sharing the work or making use of code developed by another firm. Retroactive grants should be decided on a case-by-base basis among long-standing contributors. 

The agreement in writing should have the work/revenue splits defined. These will live on the HLF wiki. A new splitter contract should be deployed by the grantor for each grant to be received. Gas can be paid for by recipients as needed for contract deploy. If the grantor cannot interface with a splitter, the primary grantee may deploy one on their behalf and use the splits defined in the contributor grant agreement.