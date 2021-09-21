# DynamicPullRequests

Demo that creates resource groups for each environment. When a PR is created, a special PR resource group is created, MyApplicationPR##, where ## is the PR number.

- MyApplicationDev
- MyApplicationQA
- MyApplicationProd

Use https://github.com/samsmithnz/GitHubWebhook to clean up the PR resource group after the pull request is closed.

## The problem we are solving:

Many organizations have very large applications, with shared resources - particularly databases. 

A typical CI/CD process looks like this: Some work is done, a build is compiled and tested, then deployed to dev to confirm integration, deployed to QA to for final testing, before being deployed to production.
![image](https://user-images.githubusercontent.com/8389039/134181358-6c59701d-782c-4cf5-843b-9de5ec1807a5.png)

This works perfectly with one developer - but as the team starts to grow, Dev becomes a bottle neck. Multiple developers can step on each others changes, and big changes break a lot of people. Isn't there a better way? What if we could create a development environment for each developer? Furthermore - using the cloud, this doesn't need to be a sustained environment, it only needs to live for the lifetime of a feature branch/ PR. Note that this does require good DevOps practices - in particular, short lived branches. 
![image](https://user-images.githubusercontent.com/8389039/134181964-da86df40-a0c5-4603-a75e-bc4ab571ea89.png)

The new workflow is: 
1. developer creates a new feature branch
2. developer starts their work. When ready (note - not nessecarily "done"), the developer pushes and creates a draft PR. 
3. This triggers the CI/CD pipeline. Note that only the PR job runs
   ![image](https://user-images.githubusercontent.com/8389039/134182299-e26a2585-d00d-4ceb-97bb-f11d60b2708d.png)
4. The PR job creates a new and unique resource group just for this PR






