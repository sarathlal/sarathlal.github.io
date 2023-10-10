---
title: Streamlining Development - Our Journey with Git, Bitbucket, and Jira
layout: post
tags:
  - git
  - Project management
  - Development
--- 

In our development team, we've recently made a significant change to how we work. We've adopted the `Git Feature Branch Workflow`, along with `Bitbucket` and `Jira`. These tools have transformed how we build software, making it easier to collaborate, manage tasks, and maintain a structured codebase.

Here are the steps:

### Set Up the Repository:

1. Create a Git repository on Bitbucket to host our project's codebase.
2. Invite team members to the repository, granting them appropriate access levels.

### Create the Jira Project:

1. Set up a Jira project to manage tasks, issues, and project tracking.
2. Integrate the Jira project with the Bitbucket repository to link code changes to specific tasks/issues.

### Branch Naming Convention:

Establish a clear and consistent branch naming convention.

For example:

1. `feature/<Jira-Issue-Key>-<short-description>` for feature branches.
2. `bugfix/<Jira-Issue-Key>-<short-description>` for bug fix branches.
3. `hotfix/<Jira-Issue-Key>-<short-description>` for critical hotfix branches.

### Workflow:

#### Main Branches:
1. *master*: Represents the production-ready codebase.
2. *develop*: Integration branch for ongoing development and testing.

#### Feature Branches:
Developers create feature branches from develop to work on specific tasks or features.

#### Bug Fix Branches:
Developers create bug fix branches from develop to address specific issues.

#### Hotfix Branches:
For critical production fixes, create hotfix branches from master.

### Development Process:

#### New Feature/Bug Fix:
1. Developers create a new branch from develop or master, depending on the nature of the task.
2. Work on the feature/bug fix and commit changes to the branch.
3. Regularly push the branch to Bitbucket to enable collaboration and backups.

#### Code Review:
1. Open a pull request (PR) on Bitbucket when the feature/bug fix is ready for review.
2. Assign the PR to one or more team members for review.
3. Team members review the code, provide feedback, and request changes if necessary.
4. Developers make adjustments based on feedback until the PR is approved.

#### Merge to Develop:
1. Once the PR is approved, merge the feature/bug fix branch into develop.
2. Test the changes in the develop branch to ensure everything is working as expected.

#### Release:
1. When the develop branch is ready for release, create a release branch from develop.
2. Test the release branch thoroughly.
3. Merge the release branch into master and tag it with a version number.
4. Deploy the code from master to production.

#### Hotfix:
1. For critical production issues, create a hotfix branch from master.
2. Make the necessary changes in the hotfix branch.
3. Merge the hotfix branch back into both master and develop.
4. Deploy the code from master to production.

### Jira Integration:
1. Link Jira issues to related pull requests on Bitbucket.
2. Add commit messages or branch names that include Jira issue keys to automatically link them to corresponding issues in Jira.

### Documentation:
1. Encourage developers to maintain comprehensive documentation.
2. Document the workflow and update it as needed to ensure everyone follows the same process.

By following this workflow, our team can maintain a structured and collaborative development process, making it easier to track progress, manage code changes, and deploy releases.
