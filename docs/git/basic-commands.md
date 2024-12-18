# Basic Commands

## Git Configuration

### Set up your name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "Your Email"
```

## Create a new repository

To create a new repository, simply run `git init` in the directory you want to version control.

For example:

```bash
mkdir myproject
cd myproject
git init
```

## Basic Workflow

!!! note
    My suggestion is to use VSCode which has integrated support for Git. You can stage and commit changes directly from the editor and you don't need to remember any of these commands.
    VSCode also has a useful extension called GitLens which allows you to see the history of a file when you are editing it and who made the changes.

Here is an example of a basic workflow if you were doing things manually using Git.

### Create a new file

```bash
echo "Hello, World!" > README.md
```

### Add the file to the staging area

```bash
git add README.md
```

### Commit the file

```bash
git commit -m "Initial commit"
```

## Check the status of your repository

```bash
git status
```

## Branching

Within a git repository, you can create branches to work on different features or bug fixes. Branching allows you to isolate changes and work on them independently.

For branching strategy I suggest you consider the GitHub flow model. <https://docs.github.com/en/get-started/using-github/github-flow>

When you first create a repository, you are on the `main` branch. You can create a new branch using the following command:

```bash
git checkout -b new-branch
```

This command creates a new branch called `new-branch` and switches to it.

You can switch between branches using the following command:

```bash
git checkout <branch-name>
```

To see a list of branches in your repository, run:

```bash
git branch
```
