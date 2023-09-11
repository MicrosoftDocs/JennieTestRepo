---
title: GitHub issues automation
description: Learn how to use the GitHub issues automation app.
author: meganbradley
ms.author: mbradley
ms.date: 09/11/2023
ms.topic: conceptual
ms.prod: non-product-specific
#A freshness review for this article was performed on 07/21/2021. No changes were made for this review.
#The Acrolinx score for this article was already at 98 on 07/21/2021. A score of 85 or above is required for merge going forward.
---

# Use the GitHub Issues Automation app

The GitHub Issues Automation app works with the [GitHub issues documentation control](github-issues-feedback.md). The app helps manage customer feedback issues. The goal of the app is to partially automate triage and management processes. The app also allows Microsoft employees to take action on issues with only Read permissions to a repo.

When installed on a repo, the app provides the following functionality.

## Service and product labeling

In docs articles, we use metadata to indicate the product or service the article applies to. When a customer submits a docs feedback issue via the feedback control, a Details pane is generated that includes any values for the `ms.service`, `ms.subservice`, `ms.prod`, or `ms.technology` attributes in the article. The issues automation app reads this information from the issue's details and applies a label for each attribute present. The label consists of the attribute value plus a suffix indicating whether it's a service, product, and so on:

- `ms.service`: **value/svc**
- `ms.subservice`: **value/subsvc**
- `ms.prod`: **value/prod**
- `ms.technology`: **value/tech**

For example, if an article has `ms.service` set to "backup", it will be labeled as follows:


These labels are used for triage.

## Default prioritization labeling

When you create a new GitHub issue using the feedback control, an automatic priority label is added to the issue when it's created. The priority label is based on page views.

- **Pri1** is assigned if the article listed in the issue's details is in the top 25% of page views for the repository. The **Pri1** label is also assigned to issues for articles that were first published during the preceding 45 days.
- **Pri2** is assigned if the article is in the second 25% of page views for the repo.
- **Pri3** is assigned to articles in the bottom 50% of page views for the repo. The **Pri3** label is also assigned to issues that users create directly in GitHub, not using the feedback control. 

Based on your knowledge of your space, current priorities and committed work, and the effort addressing an issue will take, you can use the hashtag comments in the next section to change the priority of an issue you're responsible for.

The default priority labels should help you understand the relative effect of working on a particular issue - most customers see content labeled **Pri1**.

## Hashtag commands for managing issues with Read permissions

Learn platform repos often have a large number of contributors, and it's not practical to grant Write permissions to all of them. As such, the issues automation app provides several hashtag commands. The commands enable Microsoft employees to assign, triage, and close issues with only Read perms.

|Command              |Usage    |
|---------------------|---------|
|`#assign:<GitHubID>` |Add a GitHub ID to the command, such as `#assign:tysonn`. This command assigns the issue to that person.<br>![assigned to Tyson.](media/assigned-issue.png) |
|`#reassign:<GitHubID>`|Assigns the issue to the specified GitHub user and removes other assignees.|
|`#pri1`               |Adds the **Pri1** label and removes **Pri2** or **Pri3** if present.|
|`#pri2`               |Adds the **Pri2** label and removes **Pri1** or **Pri3** if present.|
|`#pri3`               |Adds the **Pri3** label and removes **Pri1** or **Pri2** if present.|
|`#please-close`      |Closes the issue.|
|`#please-open`       |Reopens a closed issue.|
|`#label:"custom label text"`|Applies a label up to 200 characters. It can be a new label or one that already exists in the repo.|

To run these operations, type the commands in unformatted text in a comment in the issue conversation.

To allow users to provide instructions related to these commands, the commands don't work within the following formatting:

- Markdown inline code (`)
- Markdown code block (```)
- Markdown bold (**)
- Markdown italic (*)
- Any level Markdown header (# - ######)
- Any HTML element

So, if you need to tell someone how to use these commands, just put them inside formatting, like this:
