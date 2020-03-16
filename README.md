# Git Etiquette

## Branching & Merging Guidelines

Setup repository with a `master` branch and a `dev` branch. `dev` should be made the default branch.

All development should be worked on in respective branches and merged into `dev`. See [branch naming](#heading=h.mc7j46egek7) and [merging guidelines](#heading=h.r89cnkyci52b) below.

`Master` should contain the most recent published/released copy. See [merging guidelines](#heading=h.r89cnkyci52b) below.

### Branch Naming

`category/master`

`category/github_username/short_description`

* `category` examples: `sample_code`, `guidebook`

    * keep this consistent within a project

    * each `category` should have its own master branch

* `short_description` should explain what `github_username` is working on in that branch

### Merging Guidelines

#### Pull Requests

[Creating a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)

[Merging a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/merging-a-pull-request)

#### Merge Cases

##### Merging user branches into `category/master` branches

1. Pull request: select `merge pull request` option

2. Via command line: Using `merge` will maintain the true history of the development work.

```sh

git checkout category/github_username/short_description

git merge category/master

```

##### Merging `category/master` branches into `dev`

1. Pull request: select `squash and merge` option

2. Via command line: Using `rebase` will maintain a linear timeline for clarity. Squash new commits into one during the interactive rebase.

```sh

git checkout category/master

git rebase -i dev

```

Merging `dev` into `master`

1. Pull request: select `merge pull request` option

2. Via command line:

```sh

git checkout dev

git merge master

```

### Reference Material

#### [Merging vs. Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

[Proposing changes to your work with pull requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/proposing-changes-to-your-work-with-pull-requests)

## Commit Messages

Git commit messages should be thought out and not rushed. This message provides other users with a way to understand what changes you made in your commit.

A proper git commit message should follow a standard format.

The standard commit message is as follows:

`type(category): subject — footer` for example: `feat(guidebook): added title-page`

### Type

* `feat` — A new feature.

* `fix` — A bug fix.

* `docs` — Changes to only documentation.

* `style` — Changes to formatting (missing semicolons, etc.).

* `refactor` — A code change that neither fixes a bug nor adds a feature.

* `test` — Adding missing or correcting existing tests.

* `chore` — Change to build process or auxiliary tools, or maintenance.

### Category

This should correspond with the [branch names](#heading=h.mc7j46egek7).

### Subject

The subject should be limited to 50 characters and be descriptive of the changes. If there are multiple things changed, consider splitting into smaller commits (use `git add -p`).

### Reference Material

[Git Workflow Etiquette - Better Programming](https://medium.com/better-programming/git-workflow-etiquette-f22d96b8b0b8)

## Useful Git Commands

```sh

git add -p                 # stage only some changes within file(s)

git rebase -i HEAD~n       # can be used to squash last n commits

git reset --soft HEAD^     # undoes the last commit and saves stage

git stash, git stash pop   # temporarily saves local changes

```

