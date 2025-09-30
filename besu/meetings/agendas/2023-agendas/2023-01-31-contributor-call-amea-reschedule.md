# 2023-01-31 Contributor Call - AMEA Reschedule

# Grants

- Work-share decided amongst contributors that are interested in pursuing a grant
  - I.e. CSI pursues this grant and is the only group working on it, takes full split. 
  - I.e. CSI, Swirld Labs, ETC Co-Op decide to pursue a grant as Besu project, then split the grant based on agreed-upon work share. 
  - Make use of transparent splitter contracts to divide the funds 
  - Agreements in writing shared amongst contributors in advance 
- Arbitration by grantor as needed, since it is their funding. This is a fail-over mode. 
- Transparency is key - discussions to be done on Discord or on calls recorded/with shared notes

# Dependency Injection/Inversion of control

- How will DI help us?
  - Constructor bloat
  - Protocol builders/schedules everywhere
  - Massive builders, tons of components are touched by plumbing for multiple use-cases
- Spring - How will this help?
  - Spring POC - [https://github.com/hyperledger/besu/pull/4697](https://github.com/hyperledger/besu/pull/4697)
  - Won't help with the best dependency graphs
  - Dagger is way more light-weight
  - Spring is infectious in the code-base (turns it into a spring project)
  - Security issue in adding new dependencies (SPRING)
    - Spring has its own dependencies
    - Supply chain attack
  - Refactor of the code is useful anyways to address architectural challenges - THEN add DI - starting with DI instead of evaluating a refactor or the architecture is not the right way to go
  - Diego - Spring too big, maybe useful for some use-cases
- Danno - 3 Options for DI
  1. Dagger 2
  2. Spring (echoing concern of Diego)
  1. Might be heavyweight and *not* useful
  4. Rebuild protocol scheduler and refactor as an engineering challenge
  1. Biggest task is analyzing this
  - EVM
  - Data-structs/methods don't require complex assembly
  - Guice DI (DON'T DO IT
  - Library use-cases need to be "framework free"
  - Creating dependencies is more issues and reduces performance
  - VERSIONING DEPENDENCIES
- Gary
  - DI as a splitting off point for modular use-cases
  - Better for handling privacy code

   

|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22156068/GMT20230131-010025_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22156068&fileName=GMT20230131-010025_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22156068&fileName=GMT20230131-010025_Recording.transcript.vtt) | File [GMT20230131-010025\_Recording.transcript.vtt](/wiki/download/attachments/22156068/GMT20230131-010025_Recording.transcript.vtt?api=v2) | Jan 31, 2023 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22156068/GMT20230131-010025_RecordingnewChat.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22156068&fileName=GMT20230131-010025_RecordingnewChat.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22156068&fileName=GMT20230131-010025_RecordingnewChat.txt) | Text File [GMT20230131-010025\_RecordingnewChat.txt](/wiki/download/attachments/22156068/GMT20230131-010025_RecordingnewChat.txt?api=v2) | Jan 31, 2023 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22156068)