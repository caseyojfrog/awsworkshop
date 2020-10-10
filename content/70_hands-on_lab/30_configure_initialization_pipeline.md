---
title: "Configure the Initialization Pipeline"
chapter: false
weight: 30
---

Next, we will update the lab pipelines to add your new GitHub and Artifactory integrations. In previous steps, you [forked and cloned the lab repositories.](70_jfrog_devops_hands-on_lab/1_fork_workshop_repos.html) We will modify the initialization pipeline in your forked Horae repository to add these integrations.

1. In your local git directory, open Horae/pipelines/base_init.yml in an editor.
2. Update the resources section of the file to use your forked repositories. Change the _path_ to use your username.

```
resources:  
  - name: demo_gitRepo  
    type: GitRepo  
    configuration:  
      path: [your_Github_username]/Horae  <<<--- CHANGE HERE
      gitProvider: GitHub  
  - name: gitRepo_code  
    type: GitRepo  
    configuration:  
      path: [your_Github_username]/project-examples  <<<--- CHANGE HERE 
      gitProvider: GitHub
      branches:  
        include: eplus-v2-orbitera 
```

3. Save your changes.

4. In your terminal, git add, commit and push your changes.

```
$ git add .
$ git commit -m 'Updated repository paths.'
$ git push
```
5. Go to https://github.com/[username]/Horae/blob/master/pipelines/base_init.yml and verify your changes were made and pushed to your GitHub repository.

We are now ready to add and execute your pipelines with JFrog Pipelines.