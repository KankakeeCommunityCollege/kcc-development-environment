
# Publishing Branch Workflow

> *Last updated on **11/28/2022***

- [Publishing Branch Workflow](#publishing-branch-workflow)
  - [Create a `publish` branch](#create-a-publish-branch)

We use a `publish` branch to create a review/approval-workflow in CloudCannon.

Every project that has the publishing workflow has two main branches:
- `master`
- `publish`

The `master` branch is used to stage and preview changes. Once the edits are finalized they can be merged into the `publish` branch.

Each project has three website definitions in CloudCannon, for example **Academics Edit**, **Academics Admin**, and **Academics FTP**.

The **Edit** and **Admin** sites sync with the `master` branch. In other words, if you make an edit using CloudCannon and save the change it will commit and push them back to the `master` branch.

The **Admin** site in CloudCannon has a **"Publish" button** which gives users the ability to merge the `master` branch into the `publish` branch.

The **FTP** site syncs changes with the `publish` branch. It's also setup to FTP a successful builds to Web03 (which is where our website is publicly hosted.) The *FTP* sites are never used to make edits, instead **their sole purpose is to build and FTP any changes seen in the `publish` branch.**

<p align="center">
  <img src="../assets/img/publishing-workflow-infographic-with-web03.png" alt="Info-graphic of project architecture">
</p>



-----

## Create a `publish` branch

When developing locally, you need to setup a `publish` and `master` branch on your computer. You can develop in the `master` branch or create a new branch.

After edits are finalized, they should be merged into the `publish` branch so that CloudCannon can FTP the updates.


-----

[Back to main README](https://github.com/KankakeeCommunityCollege/kcc-development-environment)

