---
title: "Recovering Code from Deleted GitHub Repositories"
date: 2024-08-29T00:01:28-05:00
draft: false
tags: ["programming", "github", "open source"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "Learn how to recover code from GitHub repositories that were once public and open source using publicly documented techniques."
disableHLJS: false
disableShare: false
hideSummary: true
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
editPost:
    Text: "Suggest Changes"
    appendFilePath: true
---



Recently, one of Wave's previously public and open-source GitHub repositories, which powered a popular Terraform module[^1], was either deleted or made private[^2]. As an employee of Wave and, more importantly, a publicly listed member of their GitHub organization (@waveaccounting), I’ve been receiving a lot of questions about this.

While I can’t comment on why or whether the repository was either deleted or made private, I can show you how to access the last public version of the code using only publicly available information. This article is intended to help the broader open-source community while ensuring that I stay true to any confidentiality agreements I may have signed. Importantly, no confidential information is shared here—everything discussed is publicly documented and accessible to anyone.

## Understanding the Technique: Accessing Data from Private or Deleted Repositories

Even after a repository is either deleted or made private, some of its data can still be accessed through public forks or specific commit references. This is a somewhat hidden feature of GitHub, but it’s entirely legal and well-documented.

Truffle Security has published a detailed report on how anyone can access deleted and private repo data on GitHub using publicly available tools and information[^3]. This technique allows you to retrieve the last public version of a repository.

Now, let’s walk through how to use this technique to access the code you need.

## Step 1: Finding the Commit Hash

The first step is to find the commit hash of the version you're looking for. You might find this hash in your existing project code or logs. If not, the Wayback Machine can be a helpful tool.

By searching for an archived version of the repository on the Wayback Machine, you can often find the commit hash in the HTML source. In this instance, within the last Wayback Machine snapshot[^4] from July 6, 2022, the commit hash `e2aa7006e762f1b822256612b61bd1b10ff4fa09` was embedded in the HTML.

Since the latest version of the module was published months earlier, on January 7, 2022, this hash should correspond to that version.

## Step 2: Finding a Public Fork

Next, you'll need to find a public fork of the repository. This is crucial because the fork will likely contain the same code as the original repository.

On the Terraform module page, it’s noted that the module is managed by a former Wave employee. By searching through his GitHub profile, we found a repository that matches the original name.

Here’s [@mwarkentin's fork](https://github.com/mwarkentin/terraform-aws-chatbot-slack-configuration). This fork is likely a copy of the original repository before it was made private. We can't tell for sure since GitHub updates the designated parent fork when the original is deleted or made private[^5].

## Step 3: Combining the Pieces

With the commit hash and the public fork in hand, you can now access the exact version of the code you need. When you check out the forked repository, you’ll find a commit message like this:

```
Merge pull request #9 from @waveaccounting/release-1.1.0

1.1.0 release prep
```

This version number matches the published version of the module that you’re looking for and confirms that you’ve found the correct code.

## A Note on Commit Hashes

While the commit hash found in the Wayback Machine appears legitimate, it’s always a good idea to verify it against the commit hash you might find in your project's lock file or other records. This ensures that you're retrieving the exact version of the code that your project depends on, reducing the risk of discrepancies.

## Conclusion

Using only publicly available data, it's possible to access code from a repository that was once public. No confidential information is needed or used—everything discussed here is part of the public record.

This method highlights the importance of transparency in open-source projects and ensures that code, once shared publicly, remains accessible under its original license.

If you have any further questions, feel free to reach out. Please note that this article relies entirely on public information, with no confidential details shared.


[^1]: Terraform module on the Terraform Registry: [https://registry.terraform.io/modules/waveaccounting/chatbot-slack-configuration/aws/latest?tab=resources](https://registry.terraform.io/modules/waveaccounting/chatbot-slack-configuration/aws/latest?tab=resources).
[^2]: Original GitHub repository link (now broken): `https://github.com/waveaccounting/terraform-aws-chatbot-slack-configuration`.
[^3]: Truffle Security report on accessing deleted and private repo data on GitHub: [https://trufflesecurity.com/blog/anyone-can-access-deleted-and-private-repo-data-github](https://trufflesecurity.com/blog/anyone-can-access-deleted-and-private-repo-data-github).
[^4]: Wayback Machine snapshot of the repository: [http://web.archive.org/web/20220115035330/https://github.com/waveaccounting/terraform-aws-chatbot-slack-configuration](http://web.archive.org/web/20220115035330/https://github.com/waveaccounting/terraform-aws-chatbot-slack-configuration).
[^5]: GitHub documentation on what happens to forks when a repository is deleted or changes visibility: [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility#changing-a-public-repository-to-a-private-repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility#changing-a-public-repository-to-a-private-repository).
