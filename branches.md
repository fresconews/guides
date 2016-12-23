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
    - Master acts as the working copy of the app in production and should always be kept this way. Master should always remain as the working copy so that there is a line for line version of what's currently running in the production environment.
- Dev/Development (codebase, with developer tokens enabled, branched off master)
    - This codebase contains all of the environmental variables for testing purposes and is used to put together new features/builds. This branch should be used for active development and large scope features while keeping the master branch intact with what's running production. Feature branches can be merged into development with others to preperare a deployment that will then be sent off to staging.
- Staging
    - The staging branches acts as the preparation branch before deploying to production. When new code is being written or a feature is being developed, it should always be merged into staging first so that testing can be done on what will become the master (production) codebase. Think of the staging branch as a way of simulating your changes in the production codebase without actually deploying to production.
- Features
  - Branched off of master, used for each block of new/changed code, as small as necessary.
  - Need to be tagged with a version number to designate which release the feature will be a part of
  - Naming convention: `feature-first-feature`, `feature-second-feature`, `feature-ios-550` (story number)
- Hotfixes / Bug fixes
  - Branched off of the production codebase (master)
  - Need to be tagged with a version number to designate which release the feature will be a part of
  - Naming convention: `hotfix-signup`, `hotfix-push-notifications`

## Tags

Tags should be used to designate a commit to a version release. When you're about to merge your release, tag the commit with the version number so you have a reference of the commit the version originates from. 

## Features
When you embark on a new feature it should always be branched off of a working copy of the app. **Don't** pile up your new code into one branch or working copy! If you do this, you'll end up having to make sure a **ton of new** code works perfectly before even being able to even push it to production - and nobody wants that. You want your features to be isolated so you can push them independently and amongst other additions from the rest of the team.

### Example

> Say my new feature is adding the ability to post my gallery to Instagram. To start this out, I'll branch off of master and create a 
**feature branch** called `feature-instagram-post` and work off of that. When I'm finished building the feature I can test it independently on this branch or alternatively merge the feature branch into any other branch (dev, staging) and test it off of there. But because the 
feature has been made independent of other code in development I'm free to push it to production whenever it's ready.

## Bug Fixes & Hot Fixes
Depending on the timeline for a bug fix, you want to either branch it off of the master or development branch. If you're fixing a critical bug you should branch off the bug as a **hotfix branch**. Hotfix/Bug fixes should be prefixed with `hotfix-` to indicate what the branch is for. So if your bug/hot fix needs to go immediately to the production deployment — first, branch it off of master and and write your fix, and second, merge the fix into both the environment you need to deploy it in (master) **and** the development branch so you have your latest changes across the repositiory. You can also merge the master branch into your development branch to get the latest fixes (we talk about this more in **Propogating Fixes**)

## Keeping up to date

### Working with other engineers
If you're working with other engineers on the same repository make sure to pull their new changes if it'll affect the environment you'll be merging back into when you're finished.

#### Example
> If you've branched off of the **master** branch to build your new feature and while you're working another engineer pushes to the master 
branch with some new features, you'll want to merge the branch back into yours so that you have the latest copy in your working codebase. Otherwise you'll be  subject to pulling all of the new code from the master branch after you finish, and this might disrupt your workflow or potentially delay the feature's rollout because of potential merge conflicts or changes to the code you were unaware of.

### Propagating Fixes
When hot fixes and/or bug fixes are made on other branches, it's extremely important to make sure you capture these changes on the main branches (master, staging, development). One of the most troubling things to deal with is not capturing all changes made on the fly. The easiest solution is to make sure that after every hot fix is made you merge that fix into the main branches so the change is propagated to all upcoming versions of the codebase.

## Dos and Donts
1. Don't use force push
2. Do delete branches after you've merged - try to keep the branch list groomed and tidy!
3. Don't create user branches
4. Don't go for extended durations without a pull from the relevant branch
