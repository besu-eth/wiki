# Contributing Guidelines-

![](https://lf-hyperledger.atlassian.net/wiki/plugins/servlet/confluence/placeholder/unknown-macro?name=redirect&locale=en_US&version=2)

First off, thanks for taking the time to contribute! 

The following is a set of guidelines for contributing to Hyperledger Besu. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document.

## 

- [](#page-09fec079-781b-4b44-9654-d40ec9ebd1b2)
[](#ContributingGuidelines--)- [](#page-f470f967-360d-4767-9a3d-ee20198047f8)[Code of Conduct](#code-of-conduct)
- [I just have a quick question](#i-just-have-a-quick-question)
- [How to Contribute](#how-to-contribute)
  - [Reporting Bugs in the Doc](#reporting-bugs-in-the-doc)
    - [Before Submitting A Bug Report](#before-submitting-a-bug-report)
    - [How Do I Submit A (Good) Bug Report?](#how-do-i-submit-a-good-bug-report)
  - [Suggesting Enhancements](#suggesting-enhancements)
    - [Before Submitting An Enhancement Suggestion](#before-submitting-an-enhancement-suggestion)
    - [How Do I Submit a (Good) Enhancement Suggestion?](#how-do-i-submit-a-good-enhancement-suggestion)
  - [Your First Contribution](#your-first-contribution)
  - [Contribution Workflow](#contribution-workflow)
  - [Pull Requests](#pull-requests)
- [Documentation Style Guide](#documentation-style-guide)

## Code of Conduct

This project and everyone participating in it is governed by the [Hyperledger code of conduct](https://lf-hyperledger.atlassian.net/wiki/display/HYP/Hyperledger+Code+of+Conduct). By participating, you are expected to uphold this code. Please report unacceptable behavior according to [Incident Procedure](https://lf-hyperledger.atlassian.net/wiki/display/HYP/Hyperledger+Code+of+Conduct#HyperledgerCodeofConduct-IncidentProcedure).

## I just have a quick question 

**Note:** Please don't file an issue to ask a question. You'll get faster results by using the resources below.

- [Hyperledger Besu documentation](https://besu.hyperledger.org/)
- [Hyperledger Besu chat](https://chat.hyperledger.org/channel/besu)

## How to Contribute

### Reporting Bugs in the Doc

This section guides you through submitting a documentation bug report. Following these guidelines helps maintainers and the community understand your report, reproduce the behavior, and find related reports.

Before creating documentation bug reports, please check the [before-submitting-a-bug-report](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22154106/Contributing+Guidelines-#ContributingGuidelines--before-submitting-a-bug-report) checklist as you might find out that you don't need to create one. ,When you are creating a documentation bug report, please [include as many details as possible](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22154106/Contributing+Guidelines-#ContributingGuidelines--submit-a-bug-report).

#### Before Submitting A Bug Report

- **Confirm the problem** clear the cache of your browser and check if the issue is still there. You can also disable all your browser plugins and see if the bug still happens.
- **Perform a** [cursory search of project documentation issues](https://jira.hyperledger.org/browse/BESU-111?jql=project%20%3D%20BESU%20AND%20component%20%3D%20besu-docs) to see if the problem has already been reported. If **the issue is still open**, add a comment to the existing issue instead of opening a new one.

**Note:** If you find a **Closed** issue that seems like it is the same thing that you're experiencing, open a new issue and include a link to the original issue in the body of your new one.

#### How Do I Submit A (Good) Bug Report?

Bugs are tracked as [Jira issues](https://jira.hyperledger.org/projects/BESU/issues/BESU-111?filter=allopenissues).

Explain the problem and include additional details to help maintainers reproduce the problem:

- **Use a clear and descriptive summary** for the issue to identify the problem.
- **Describe the exact steps which reproduce the problem** in as many details as possible.
- **Provide specific examples to demonstrate the steps**. Include links, search keywords which you use in those examples. If you're providing snippets in the issue, use backticks (\`\`\`) to format the code snippets.
- **Describe the behavior you observed after following the steps** and point out what exactly is the problem with that behavior.
- **Explain which behavior you expected to see instead and why.**
- **Include screenshots or screen recordings** which show you following the described steps and clearly demonstrate the problem.

Provide more context by answering these questions:

- **Did the problem start happening recently** (e.g. after a doc update) or was this always a problem?
- If the problem started happening recently, **can you reproduce the problem in an older version of the doc?** What's the most recent version in which the problem doesn't happen?
- **Can you reliably reproduce the issue?** If not, provide details about how often the problem happens and under which conditions it normally happens.

Include details about your configuration and environment:

- **Which version of the doc are you browsing?** You can get the exact version by looking at the url.
- **What OS & Version are you running?**
- **What Browser & Version are you running?**
- **What Plugins/Extensions & Version have you installed and enabled in your browser?**

  

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion, including completely new features and minor improvements to documentation.

Following these guidelines helps maintainers and the community understand your suggestion and find related suggestions.

Before creating enhancement suggestions, please check the [before-submitting-an-enhancement-suggestion](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22154106/Contributing+Guidelines-#ContributingGuidelines--#before-submitting-an-enhancement-suggestion) list as you might find out that you don't need to create one.

When you are creating an enhancement suggestion, please [include as many details as possible](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22154106/Contributing+Guidelines-#ContributingGuidelines--how-do-i-submit-a-enhancement-suggestion).

#### Before Submitting An Enhancement Suggestion

- **Perform a [cursory search of project issues](https://jira.hyperledger.org/browse/BESU-144?jql=project%20%3D%20BESU)** to see if the problem has already been reported. If it has **and the issue is still open**, add a comment to the existing issue instead of opening a new one.

  

#### How Do I Submit a (Good) Enhancement Suggestion?

Enhancement suggestions are tracked as [Jira issues](https://jira.hyperledger.org/browse/BESU-144?jql=project%20%3D%20BESU). Provide the following information:

- **Use a clear and descriptive summary** for the issue to identify the problem.
- **Describe the exact steps which reproduce the problem** in as many details as possible.
- **Provide specific examples to demonstrate the steps**. Include links, search keywords which you use in those examples. If you're providing snippets in the issue, use backticks (\`\`\`) to format the code snippets.
- **Describe the current behavior** and **explain which behavior you expected to see instead** and why.
- **Include screenshots or screen recordings** which help you demonstrate the steps where possible.
- **Explain why this enhancement would be useful** to most users.
- **Does this enhancement exist in other docs?**
- **Which version of the doc are you browsing?** You can get the exact version by looking at the url.
- **What OS & Version are you running?**
- **What Browser & Version are you running?**
- **What Plugins/Extensions & Version have you installed and enabled in your browser?**

  

### **Your First Contribution**

Start by looking through the 'good first issue' and 'help wanted' labeled issues on the [Jira dashboard](https://jira.hyperledger.org/browse/BESU-85?jql=project%20%3D%20BESU%20AND%20labels%20%3D%20good-first-issue%20):

- \[Good First Issue\]\[search-label-good-first-issue\] - issues which should only require a few lines of code or documentation, and a test or two.
- \[Help wanted issues\]\[search-label-help-wanted\] - issues which are a bit more involved than `good first issue` issues.

When you've identified an issue you'd like to work on, ping us on [Hyperledger Besu chat](https://chat.hyperledger.org/channel/besu) and we'll assign it to you.

### Contribution Workflow

The documentation is maintained using a "*contributor workflow*" where everyone without exception contributes changes proposals using "*pull-requests*".

This facilitates social contribution, easy testing, and peer review.

To contribute changes, use the following workflow:

1. [**Fork the repository**](https://github.com/hyperledger/besu-docs/fork).
2. **Clone your fork** to your computer.
3. **Create a topic branch** and name it appropriately. Starting the branch name with the issue number is a good practice and a reminder to fix only one issue in a Pull-Request (PR).\_
4. **Make your changes** adhering to the documentation conventions described below. *In general a commit serves a single purpose and diffs should be easily comprehensible. For this reason do not mix any formatting fixes or typo fixes with actual documentation changes.*
5. **Commit your changes** using a clear commit message.
6. **Test your changes** locally before pushing to ensure that what you are proposing is not breaking another part of the doc.
  - displaying the doc with [MkDocs](https://www.mkdocs.org/) in a preview mode enables you to check the rendering as explained in the MkDocs And Markdown Guide.
7. **Push your changes** to your remote fork (usually labeled as `origin`).
8. **Create a pull-request** (PR) on the Besu doc repository. If the PR addresses an existing Jira issue, include the issue number in the PR title in square brackets (for example, `[PAN-1234]`).
9. **Add labels** to identify the type of your PR. *For example, if your PR fixes a bug, add the "bug" label.*
10. If the PR address an existing Jira issue, comment in the Jira issue with the PR number.
11. **Ensure your changes are reviewed**. *Select the reviewers you would like to review your PR. If you don't know who to choose, simply select the reviewers proposed by GitHub or leave blank and let us know on [Hyperledger Besu chat](https://chat.hyperledger.org/channel/besu).*
12. **Make any required changes** on your contribution from the reviewers feedback. *Make the changes, commit to your branch, and push to your remote fork.*
13. **When your PR is validated**, all tests passed and your branch has no conflicts with the target branch, you can **"squash and merge"** your PR and you're done. You contributed to [Hyperledger Besu documentation](https://besu.hyperledger.org/)! Thanks !

### Pull Requests

The process described here has several goals:

- Maintain documentation quality
- Fix problems that are important to users
- Engage the community in working toward the best possible documentation
- Enable a sustainable system for maintainers to review contributions
- Further explanation on PR & commit messages can be found in this post: [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/).

Please follow these steps to have your contribution considered by the approvers:

1. Ensure all commits have a [Sign-off for DCO](https://lf-hyperledger.atlassian.net/wiki/display/BESU/How+to+Contribute#HowtoContribute-TheDeveloperCertificateofOrigin(DCO)checks).
2. Follow all instructions in [PULL-REQUEST-TEMPLATE.md](https://github.com/hyperledger/besu-docs/blob/master/.github/pull_request_template.md).
3. Follow the Style Guides.
4. If required, update [CHANGELOG.md](../../content-refactor/developing/changelog.md). 
5. After you submit your pull request, verify that all [status checks](https://help.github.com/articles/about-status-checks/) are passing.

What if the status checks are failing?

While the prerequisites above must be satisfied prior to having your pull request reviewed, the reviewer(s) may ask you to complete additional writing, or other changes before your pull request can be ultimately accepted. Please refer to [Code Reviews](https://github.com/hyperledger/besu-docs/blob/master/docs/community/code-reviews.md).

## Documentation Style Guide

Doc style will be checked automatically during a build.

We have [documentation guidelines and examples](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Besu+Documentation+Style+Guide). These rules are not automatically enforced but are recommended to make the documentation consistent and enhance the user experience.

Also have a look at our MKDocs Markdown guide if you're not familiar with MarkDown syntax. We also have a number of extensions that are available in the documentation described in this guide.