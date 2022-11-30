
# Publishing Branch Workflow

> *Last updated on **11/29/2022***

- [Publishing Branch Workflow](#publishing-branch-workflow)
  - [Creating a `publish` branch](#creating-a-publish-branch)
  - [Developing locally](#developing-locally)

We use a `publish` branch to create a review/approval-workflow in CloudCannon.

Every project that has the publishing workflow has two main branches:
- `master`
- `publish`

The `master` branch is used to stage and preview changes. Once the edits are finalized they can be merged into the `publish` branch.

Each project has three website definitions in CloudCannon, for example **Academics Edit**, **Academics Admin**, and **Academics FTP**.

<p align="center">
  <img src="../assets/img/academics-project.jpg" alt="Screenshot of the Academics project in CloudCannon and its three sites — Academics FTP, Academics Admin, and Academics Edit">
</p>

The **Edit** and **Admin** sites sync with the `master` branch. In other words, if you make an edit using CloudCannon and save the change it will commit and push them back to the `master` branch.

The **Admin** site also has a **"Publish" button** which gives users the ability to merge the `master` branch into the `publish` branch.

The **FTP** site syncs changes with the `publish` branch. It's setup to FTP a successful build to Web03 (which is where our website is publicly hosted.) 

The *FTP* sites are never used to make edits, instead **their sole purpose is to build and FTP any changes seen in the `publish` branch.**

<p align="center">
  <img src="../assets/img/publishing-workflow-infographic-with-web03.png" alt="Info-graphic of project architecture">
</p>

-----

## Creating a `publish` branch

When developing locally, you need to setup a `publish` and `master` branch on your computer. You can develop in the `master` branch or create a new branch.

After edits are finalized in `master`, they should be merged into the `publish` branch and CloudCannon will then FTP the updates to our server.

When you clone a project from GitHub you get the `master` branch (KCC's default branch in GitHub.)

```bash
git clone git@github.com:KankakeeCommunityCollege/academics.git
cd academics
npm i && bundle i
# Working inside master branch
```

Create a `publish` branch and pull (assuming a `publish` branch exists in GitHub already):

```bash
git branch publish
git checkout publish
git pull origin publish
```

**Be sure to use `-u` or `--set-upstream` the first time you `push` from a new branch.**

If you are creating a local `publish` branch when none exists in GitHub, you should create and checkout the branch and do a `push` right away using the `-u` flag (long form: `--set-upstream`):

```bash
git branch publish
git checkout publish
git push -u origin master
# CONSOLE OUTPUT
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'publish' on GitHub by visiting:
remote:      https://github.com/KankakeeCommunityCollege/kcc-development-environment/pull/new/publish
remote:
To github.com:KankakeeCommunityCollege/kcc-development-environment.git
 * [new branch]      publish -> publish
branch 'publish' set up to track 'origin/publish'.
```

This ensures that when we go to sync our local files, our `pull` will come from the correct remote branch:

```bash
git checkout publish
git pull ## no need to specify branch when you pull
```


-----

## Developing locally

**This section assumes you have a `master` and `publish` branch already setup.**

When you start working in a project again you need to be sure and sync your local branches:

```bash
git checkout master
git pull
git checkout publish
git pull
git checkout publish # start developing
```

First, stage your edits and commit them to the `master` branch:

```bash
git add .
git commit -M "My wonderful commit message"
git push -u origin master # don't need -u and branch if tracking is setup
```

To make the edits live, you need to checkout the `publish` branch and merge the changes and push:

```bash
git checkout publish
git merge master
git push -u origin publish # don't need -u and branch if tracking is setup
```

-----

[Back to main README](https://github.com/KankakeeCommunityCollege/kcc-development-environment)

