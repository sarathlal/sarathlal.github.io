---
title: Trigger Bitbucket pipeline based on commits in specific branch or specific tag
layout: post
tags:
  - BitBucket
  - Automation
  - CI/CD
---

### Trigger pipeline based on commits in specific branch

    pipelines:
      branches:
        master:
          - step:
              script:
                - echo "master"
        develop:
          - step:
              script:
                - echo "work"

If we have to do same jobs for multiple branch, we can use a list of branch names. Note that there is no empty spaces in the list of branches!

    pipelines:
      branches:
        '{master,develop,feature}':
          - step:
              script:
                - echo "master, develop or feature"
        work:
          - step:
              script:
                - echo "work"

### Trigger pipeline based on tag

    pipelines:
      tags:
        '*':
          - step:
              name: "Preparing bash to scripts"
              script:
                - echo $BITBUCKET_TAG

The `$BITBUCKET_TAG` is the default variable availe in pipeline.

### Trigger pipeline based on release candidate tag

For our release canditate, we will add a tag with format like `[our-version-number]-rc[increment]`. An example is 2.9.3-rc1 etc.

    pipelines:
      tags:
        '*-rc*':
          - step:
              script:
                - echo "My tag build"
