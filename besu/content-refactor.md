# Content Refactor

It is becoming increasingly difficult to find oneself in the contribution docs for Besu.

This document tries to simplify and streamline the contributor content in order to help find oneself in the above processes.

# Docs v/s Wiki v/s Repo

These 3 places should contain 3 different *types* of content.

- **Docs** will contain content about the use of the Besu client itself
- **Wiki** will contain information concerning contributions and/or HL
- **Repo** should contain information only maintainers should be able to change. As well as anything directly tied to the codebase itself such as maintainer list, etc.

# Structure

**Current/old Besu REPO:**

```
`github.com/hyperledger/besu ├── CHANGELOG.md ├── CLI-STYLE-GUIDE.md ├── CODE-OF-CONDUCT.md ├── CODING-CONVENTIONS.md ├── CONTRIBUTING.md ├── DCO.md ├── MAINTAINERS.md ├── README.md ├── ROADMAP.md └── SECURITY.md`

```

  

 **Current/old Besu wiki:** 

The current wiki has lots of duplicate content and hard to find information. The whole wiki structure will be re-organized and content from both the current wiki and repo will be added here.

A new proposal of contributor content location.

  

* * *

**Proposed/new Besu REPO:** 

```
`├── CHANGELOG.md ├── CONTRIBUTING.md ├── DCO.md ├── MAINTAINERS.md └── README.md`

```

  

 **Proposed/new Besu wiki:** 

```
`wiki.hyperledger.org/display/BESU/Hyperledger+Besu ├── Contributing |   └── [contributing documentation] ├── Developing and Conventions |   └── [documents relevant to current contributors and maintainers] ├── Documentation |   └── [information regarding documenting, and documentation] ├── Roadmap ├── Security ├── Code of Conduct └── Useful Links`

```