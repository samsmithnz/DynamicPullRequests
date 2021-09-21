# DynamicPullRequests

Demo that creates resource groups for each environment. When a PR is created, a special PR resource group is created, MyApplicationPR##, where ## is the PR number.

- MyApplicationDev
- MyApplicationQA
- MyApplicationProd

Use https://github.com/samsmithnz/GitHubWebhook to clean up the PR resource group after the fact.
