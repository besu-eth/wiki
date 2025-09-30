# Besu Documentation Style Guide-

# Purpose of this document

This document contains guidelines to ensure the Besu documentation is consistent and well organised.

This is a living document and will evolve to better suit Besu users and contributors needs.

**Note**: Although not everything in this style guide is currently followed in the Besu documentation, these guidelines are intended to be applied when writing new content and revising existing content.

The primary audience for this document is:

- Members of the Besu team
- Developers and technical writers contributing to the Besu documentation

# Mission statement

The Besu documentation contributes to a consistent and easy to understand experience for end users. We're focused on creating a great experience for both new and expert users of Ethereum clients.

# General guidelines

The guiding principles for the Besu documentation are:

- Be consistent
- Keep it simple but technically correct
- Be proactive and suggest good practices
- Be informative and exhaustive

## 1\. Be consistent

Consistency is important to help our end users build a mental model of how Besu works. By being consistent with our word choices, visual formatting, and style of communication it helps users know what to expect when they refer to or search Besu documentation.

## 2\. Keep it simple but technically correct

Avoid technical jargon and always assume our end users may not be Ethereum experts.

This doesn't mean explaining all Ethereum concepts in our documentation. Explain Besu functionality and when an understanding of complex Ethereum concepts is required refer users to relevant resources.

For example, to explain how the EVM works, link to [ethdocs.org](http://ethdocs.org) documentation such as [https://github.com/ethereum/wiki/wiki/Ethereum-Virtual-Machine-(EVM)-Awesome-List](https://github.com/ethereum/wiki/wiki/Ethereum-Virtual-Machine-(EVM)-Awesome-List)

Simple explanations must still be technically correct.

## 3\. Be proactive and suggest good practices

Being proactive means anticipating user needs and guiding them through a process. This most often takes the form of notes or tip messages alongside the main explanation. Put yourself in the user's shoes and consider what questions you would have when reading the documentation.

Do not assume required steps are implied. Err on the side of including them if you are unsure.

Documenting good practices is also important. For example, instruct users to secure private keys and protect RPC endpoints a production environments.

## 4\. Be informative but concise

We seek a balance between providing enough relevant information to help our users develop a solid mental model of how Besu works without forcing them to read too much text or redundant detail.

To provide additional detail, use sub-sections.

# Writing style guide

We use the [Microsoft Style Guide](https://docs.microsoft.com/en-us/style-guide/welcome/) as our general guide to writing technical documentation. We take guidance from it but do not apply every rule. For example, we use title case rather than sentence case.

The Microsoft Style Guide aims for natural, simple, and clear communication.

Here are some important points we follow:

## Active voice

Use active voice. Use you to create a more personal friendly style. Avoid gendered pronouns (he or she).

## Contractions

Use contractions. For example, don’t.

Use common contractions, such as it’s and you’re, to create a friendly, informal tone.

## Recommend

It's acceptable to use "we recommend" to introduce a product recommendation. Don't use "Hyperledger recommends" or "it is recommended."

Example: Instead of This is not recommended for production code use We don't recommend this for production code.

## Directory vs folder

Use directory over folder because we are writing for developers.

## Sentence case for headings

Use sentence-style capitalization.

## Assumed knowledge for readers

We have two distinct audiences to consider when developing content:

- New to Ethereum and Ethereum clients
- Experienced with Ethereum clients other than Besu

## Avoid abbreviations

Try not to use abbreviations except for well known ones and some jargon. Don't use "e.g." but use "for example". Don't use "i.e." but use "that is".