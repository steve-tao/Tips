# Working with repository

## Clone from a remote repository

### Using SSH

Substitute ```<namespace>``` with the actual namespace.
Substitute ```<existing-project>``` with the actual project.

```shell
git clone git@gitlab.com:<namespace>/<existing-project>.git
```

### Using HTTPS

Substitute ```<namespace>``` with the actual namespace.
Substitute ```<existing-project>``` with the actual project.

```shell
git clone https://gitlab.com/<namespace>/<existing-project>.git
```

## Adding an existing project to GitHub/GitLab using the command line

Most steps are similar for both online repository.  However, there are slightly
differences in the way the remote repositories are set up.

### GitHub

Assume that we have the local repository on the master branch.

1. First, we need to ***`create a new repository`*** on GitHub.  Since there
   may be some conflicting items that can cause errors, ***do not initialize
   this new repository with README, LICENSE, or .gitignore files***.

2. Copy the remote repositoy URL from the top of the GitHub repository's
   *`Quick Setup`* page.

3. Add the URL for the remote repository where the local repository will be
   pushed.
    ```shell
    # Set the new remote
    $ git remote add origin  <REMOTE_URL>
    # Verify the new remote URL
    $ git remote -v
    ```

4. Push the local repository to GitHub.
    ```shell
    # Push the local repository up to the remote repository specified as the origin
    $ git push -u origin master
    ```

5. (Optional) Push all branches and all tags.
    ```shell
    git push --all --tags
    ```

### GitLab

Assume that we have the local repository on the master branch.

1. For GitLab, we can directly push the local repository to create a new
   repository on GitLab.
    ```shell
    git push --set-upstream https://gitlab.com:<namespace>/existing-project.git master
    ```

2. Set the remote and the URL to the new project.
    ```shell
    git remote add origin https://gitlab.com:<namespace>/existing-project.git
    ```

3. (Optional) Add the upstream (tracking) reference.  This step is to make the
   local repository to also track the remote repository.  The command is the
   same as `Pushing the local repository up to the remote repository`.
    ```shell
    git push -u origin master
    ```

4. (Optional) Push all branches and all tags.
    ```shell
    git push --all --tags
    ```