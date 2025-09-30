# Reporting Bugs

This section guides you through submitting a bug report. Following these guidelines helps maintainers and the community understand your report, reproduce the behavior, and find related reports.

When you are creating a bug report, please include as many details as possible.

> **Note:** If you find a **Closed** issue that seems like it is the same thing that you're experiencing, open a new issue and include a link to the original issue in the body of your new one.

# Before Submitting A Bug Report

- **Confirm the problem** is reproducible in the latest version of the software
- **Check [Besu documentation](https://besu.hyperledger.org/)**. You might be able to find the cause of the problem and fix things yourself.
- **Perform a [cursory search of project issues](https://github.com/hyperledger/besu/issues)** to see if the problem has already been reported. If it has **and the issue is still open**, add a comment to the existing issue instead of opening a new one.

# How Do I Submit A (Good) Bug Report?

Bugs are tracked as [issues](https://github.com/hyperledger/besu/issues).

Explain the problem and include additional details to help maintainers reproduce the problem:

- **Use a clear and descriptive summary** for the issue to identify the problem.
- **Describe the exact steps which reproduce the problem** in as many details as possible. For example, start by explaining how you started Besu, e.g. which command exactly you used in the terminal, or how you started it otherwise.
- **Provide specific examples to demonstrate the steps**. Include links to files or GitHub projects, or copy/pasteable snippets, which you use in those examples. If you're providing snippets in the issue, use backticks (\`\`\`) to format the code snippets.
- **Describe the behavior you observed after following the steps** and point out what exactly is the problem with that behavior.
- **Explain which behavior you expected to see instead and why.**
- **Include screenshots** which show you following the described steps and clearly demonstrate the problem.

Provide more context by answering these questions:

- **Did the problem start happening recently** (e.g. after updating to a new version of the software) or was this always a problem?
- If the problem started happening recently, **can you reproduce the problem in an older version of the software?** What's the most recent version in which the problem doesn't happen?
- **Can you reliably reproduce the issue?** If not, provide details about how often the problem happens and under which conditions it normally happens.

Include details about your configuration and environment:

- **Which version of the software are you using?** You can get the exact version by running `besu -v` in your terminal.
- **What OS & Version are you running?**
  - **For Linux - What kernel are you running?** You can get the exact version by running `uname -a` in your terminal.
- **Are you running in a virtual machine?** If so, which VM software are you using and which operating systems and versions are used for the host and the guest?
- **Are you running in a docker container?** If so, what version of docker?
- **Are you running in a a Cloud?** If so, which one, and what type/size of VM is it?
- **What version of Java are you running?** You can get the exact version by looking at the besu logfile during startup.
- If you are using privacy, we request some [extra information](../../besu/developing-and-conventions/archive-dev/checklist-for-reporting-privacy-issues.md).