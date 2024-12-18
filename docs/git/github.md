# GitHub Operations

Earlier, we created a repository locally on your computer. Now, we will push this repository to GitHub.

## Create a new repository on GitHub

1. Go to [GitHub](https://github.com) and log in.
2. Click on the `+` icon in the top right corner and select `New repository`.
3. Fill in the repository name, description, and choose whether it is public or private.
4. Click on `Create repository`.

## Push your repository to GitHub

1. Go back to your terminal.
2. Navigate to the directory where your repository is located.
3. Run the following commands:

```bash
git remote add origin
git branch -M main
git push -u origin main
```

This will push your repository to GitHub. You can now view your repository on GitHub.

## Pull changes from GitHub

If you are working on multiple machines or collaborating with others, you may need to pull changes from GitHub.

1. Run the following command:

```bash
git pull
```

This will pull the changes from GitHub to your local repository.

## Push changes to GitHub

If you have made changes to your local repository and want to push them to GitHub, you can run the following command:

```bash
git push
```

This will push your changes to GitHub.

## Clone a repository from GitHub

If you want to work on a repository that is hosted on GitHub, you can clone it to your local machine.

1. Go to the repository on GitHub.
2. Click on the `Code` button and copy the URL.
3. Run the following command:

```bash
git clone <repository-url>
```

This will clone the repository to your local machine.
