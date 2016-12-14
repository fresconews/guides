<p align="center" >
  <img src="https://s3.amazonaws.com/com.fresconews.v2.prod/static/images/wordmark-transparent-git4.png" alt="Fresco" title="Fresco News">
</p>

This is a guideline for organizing branches within a Git repo —— instructions on how to manage code while in development and while the application is in production to ensure full flexibility and as little overhead as possible when having to push immediate changes to a production environment. Here's a lesson on merging if you're unfamiliar with the topic — https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging

## Key Terms to know
1. Merge Conflicts
2. Merging

## Branch Structure
Every repo should be composed of three main branches — `master, staging, and development` — when starting out. The following is a list of the various types of branches that you may find yourself working with.
- Master (production codebase)
    - Master acts as the working copy of the app in production and should always be kept this way. It's imperative that it always remains as the working copy so that there is a line for line reference to what's currently running in the production environment.
- Staging
    - The staging branches acts as the pre-cursor before deploying to production. When new code is being written or a feature is being developed, it should always be merged into staging so that testing can be done on what will be the master codebase. Before a new feature or any new code is pushed to a production app, it should be merged into the staging branch prior to test how the code behaves and merges when mixed with the production environment. After successfully merging, the staging branch should be merged into the master branch.
- Dev/Development (codebase, with developer tokens enabled, branched off master)
    - This codebase contains all of the environmental variables for testing purposes and is always used to put together new deployments/builds. This branch should be used for most active development and large scope features while keeping the master branch intact with what's running production.
- Features
    - Branched off of master, used for each block of new/changed code, as small as necessary.
    - Naming convention: `master-new-feature`, `master-second-feature`
- Hotfixes / Bug fixes
  - Branched off of a working copy
  - Naming convention: `master-hotfix-signup`, `dev-hotfix-push-notifications`

## Features
When you embark on a new feature it should always be branched off of a working copy of the app. **Don't** pile up your new code into one branch or working copy! If you do this, you'll end up having to make sure a **ton of new** code works perfectly before even being able to even push it to production - and nobody wants that. You want your features to be isolated so you can push them independently and amongst other additions from the rest of the team.

### Example

> Say my new feature is adding the ability to post my gallery to Instagram. To start this out, I'll branch off of master and create a 
**feature branch** called `master-instagram-post` and work off of that. When I'm finished building the feature I can test it independently on this branch or alternatively merge the feature branch into any other branch (dev, staging) and test it off of there. But because the 
feature has been made independent of other code in development I'm free to push it to production whenever it's ready.

## Bug Fixes & Hot Fixes
Depending on the timeline for a bug fix, you may either branch it off of the master or development working copy. If you're fixing a critical bug, you should almost always branch off the bug as a **hotfix branch**. Hotfix and bug fixes should be prefixed with `hotfix-` to indicate what the branch is for. So if your bug/hot fix needs to go immediately to the production deployment - first, branch it off of master and and write your fix, and second, merge the fix into both the environment you need to deploy it in **and** the development environment so you have your latest changes across the repositiory. Alternatively, you can just merge the master branch into your development branch to get the latest fixes (we talk about this more `Propogating Fixes`)

## Keeping up to date

### Working with other engineers
If you're working with other engineers on the same repository make sure to pull their changes if it'll affect the environment you'll be merging back into when you've completed your work.

#### Example
> If you've branched off of the **master** branch to build your new feature and while you're working another engineer pushes to the master 
branch, you'll want to merge the branch back in again so that you have the latest copy in your working codebase. Otherwise you'll be 
subject to pulling all of the new code from the master branch after you finish, and this might disrupt your workflow or potentially  delay 
the feature's rollout because of potential merge conflicts.

### Propagating Fixes
When hot fixes and/or bug fixes are made on other branches, it's extremely important to make sure you capture these changes on the main branches (master, staging, development). One of the most troubling things to deal with is not capturing all changes made on the fly. The easiest solution is to make sure after every hot fix is made that you merge that fix into the main branches so the change is propagated to all upcoming versions of the codebase.

## *Do not*
1. Do not use force push
2. Do not create user branches
3. Go for extended durations without a pull request from the relevant branch
4. Leave branches hanging for a long time after they've been merged, try to keep our branch list groomed and tidy
