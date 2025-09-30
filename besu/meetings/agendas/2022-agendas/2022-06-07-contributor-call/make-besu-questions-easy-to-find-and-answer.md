# Make Besu questions easy to find and answer

## Goal of this page

- **Get feedback** from contributors with experience in Github discussions vs Discord.
- It looks like we already made an attempt of what I describe bellow at some point in the past, I would love to know **why we reverted** before making the same mistake again.

Please **provide your feedback in comments** on this page.

## Problem

- As a doc team and contributors who participate in answering questions in the Besu Discord, we find it **hard to follow the messages flow** and **find questions** **that need answers**.
- We also struggle to **redirect users to previous answers** and users don't even **search for previous answers** as the effort to do so on Discord is outpacing by far the effort to simply ask again... and again... and again.

## Suggestion

Activate, configure and use Besu **Github repos discussions.**

ConsenSys already uses this for instance for [https://github.com/ConsenSys/quorum/discussions](https://github.com/ConsenSys/quorum/discussions)

### Pros

- have **visibility** on questions that need answers
- **build a knowledge base** in the product repos itself, no 3rd party tool.
- **Search** for a previously asked question
- have a **link to a specific question** to send when users ask on Discord
- Have questions **sorted by popularity**. Users can vote making a question go up or down in the list.
- subscribe to **notifications** on a specific discussion, not the whole channel...
- **organise** with labels (sync issue, database crash, command line questions,...)
- lock a conversation if something goes wrong or we already have the best answer.
- pin questions to provide **visibility**
- create discussion from **GitHub issue** and the other way too
- get some basic **statistics** on contributions but at least we have metrics to see if it works
- **Ease search** for discussions by sorting and filtering
- makes the Discord **chat** a chat again and not a fake knowledge base that doesn't work.

### Cons

- requires a **GitHub account** to participate
- requires us to **redirect users** from discord to GitHub when we have questions (or search for them if we want to point to the same question directly)
- may require to **create a bot** later on Discord that could spot questions in the chat and search and post a link to the answer that looks like it can help...

## Implementation

If we agree that this is worth trying (we can always revert), then we **setup discussions** and **start sending the link to users** every time they asks a questions on Discord.  
**If you know the answer**, but the answer is not yet in the discussions, **add it** once the user created their question in the discussion.