# Git Exercise 1
## Pushing and Pulling - The Basics

In this exercise, you will learn the following:

- How to sign up to a based online product (we will use Github ) ✔
- Installing Git on your machine ✔
- Set your name and email in Git ✔
- Enable storing your git credentials ✔
- Creating a git repo ✔
- Cloning it locally ✔
- Creating branches ✔
- Deleting Branches ✔
- Listing Branches (local) ✔
- Listing Branches (remote) ✔
- Making changes: add (stage) / commit / push ✔

### 1. How to sign up to a based online product (we will use Github )
- Go to the GitHub website and sign up to get an account. Make a note of your account details
- Setup your personal access token (tick all the permissions). Make a note of this, you won't see it again once you leave this screen. 
- _Tip:_ you can find this in Developer Options and we cover this in the video. I use the classic personal access token. Set the expiration to _never expires_ or maximum amount of days available.

### 2. Installing Git on your machine
- You can figure this out yourself. If you're using mac, you can use brew, or just google 'how to install git on macos'. If you're on Windows, you can use an .exe file which you can find online.
- Test the installation by going to your cli / terminal / command line, and type 'git'. This should yield the full list of options you have available in a list.

### 3. Set your name and email in Git
- When you make commits, it helps to know who made the commit and what their email is. Rather than use your default credentials from github account, OR defaulting to your login name etc, we will store a set name and email in the **- - global config**. 

```
git config --global user.name "Mary Jane"
git config --global user.email "mary.jane@example.com"
```

### 4. Enable storing your git credentials
- When we have a remote (GitHub) hosted git repository, they are often private and changes require having credentials. Even public repositories require credentials by the owner to change contents and add / remove files to the repo
- Often when we do a `git push`, we have to log-in to GitHub. To avoid logging in repeatedly, you can enable storage of credentials which will ensure you don't have to keep logging in
- With this option, **you** have to be aware that git stores the credentials in a plain text file, which can be exploited by malicious third-party code or others who may have acess to your machine
- Finally, with this option, if your login is _unsuccessful_ then your git pull / push will fail, which will **remove the stale (current) credential from the store**, and successful future login credentials will then subsequently be stored.
- simply run:
```
git config --global credential.helper store
```

### 5. Creating a git repo
- Create a _private_ git repo in GitHub called 'myfirstrepo'
- Go through the options and allow it to create a default 'main' branch with a ReadMe.md tile to begin with

### 6. Cloning it locally
- Go on to the 'myfirstrepo' GitHub page which should be defaulted to the _main_ branch view. There's a green button called '<>Code'. Click on that - it's a drop-down. Under **clone**, copy the 'HTTPS uri
- Go back to your local machine's terminal, and create a new directory called 'repos' e.g. `mkdir ~/repos` (`~` is linux speech for _my home directory_, but this is not a Linux course!)
- Go into the repos directory e.g. `cd repos` (`cd` is linux speech for _change my directory to_)
- Once inside the repos directory run the following with your https uri copied above:
`git clone https://github.com/yourpathhere`
- This will now download your GitHub repo and its content in a **local repo** and manage link it to the **remote repo**, where you will be able to run git commands and manage the contents here

### 6. Creating branches 
- Now that you have a local version of your remote repository, you can go ahead and create a branch. There are two ways to create a branch. Run these commands one at a time:
    - `git status` - this will tell you the **status of the branch you are on**, but also indicate what local branch you are on **(main)** and it's mapping to the remote branch **(origin/main)**:
        ```
        $ git status
          ...On branch main
          Your branch is up to date with 'origin/main'
        ```
- We're now going to branch _off of main_ (also we can say we are **branching from main**). Run the following:
    - use the `branch` subcommand to add a branch called _hello_
        ```
        $ git branch hello
        ```
        If you run `git status` again you can see that we are still on the `main` branch. This is because we need to switch to the `hello` branch we created. But, first let's list all the local branches available. Run:
        ```
        $ git branch
          hello
          * main
        ```
        You can see the * is on the main, because we are currently sitting **on** the main branch. Now, run `git checkout hello` to switch to the new branch we just created.
        ```
        $ git checkout hello
          Switched to branch 'hello'
        ```
        And that's it! You've created a branch and switched to it. 
-  An easier way to do this is to use the `git checkout -b <new_branch_name>` command. It will create the new branch **and** switch to it in one command. 
    -  Run this command to find out how this works:
        ```
        $ git checkout -b newFeatureBranch
          Switched to a new branch 'newFeatureBranch'
        ```
        This has now created a new branch off-of `main` and switched to it. You can confirm this by running `git status`
        ```
        $ git status
          On branch newFeatureBranch
          nothing to commit, working tree clean
        ```

### 7. Deleting Branches 
- Now that we know how to create branches, let's go ahead and delete them. First try to delete the branch `newFeatureBranch` by running`git branch -d newFeatureBranch`. 
- It shouldn't work! 
- This is because you're currently already on this branch. You can't really delete the branch that you're currently on. Run `git status` to check which branch you are on. 
- You can switch to another branch and then delete the `newFeatureBranch` You can do this by running: 
    ```
    $ git checkout hello 
      Switched to branch 'hello'
    $ git branch -d newFeatureBranch
      Deleted branch newFeatureBranch (was 67614c8).
    ```
- That worked. You can see that it's deleted by...

### 7. Listing Branches (local)
- You can list all local branches simply by running `git branch` as we have done above. You will see that you now have only two branches: `main` and `hello` which was branched from `main`. 
    ```
    $ git branch 
      * hello
        main
    ```

### 8. Listing Branches (remote)
- Although we can list local branches, we can also list the branches on the _origin_. The word **origin** in git world means 'remote' - that's the repo hosted on the internet. As we did not push our `hello` branch, only the remote branch`main`, exists in our GitHub repo. You can run the `git branch -r` command to list all remote branches.  
    ```
    $ git branch -r
      origin/HEAD -> origin/main
      origin/main
    ```
- You can see only `origin/main` exists. But there is a pointer `origin/HEAD` too! This is just a pointer -- it is pointing too the branch `main` on the remote repo. 
- **BONUS HOMEWORK:** Whatis the point `origin/HEAD` and what's it purpose?
- You can go ahead and go to the GitHub UI in your browser, and you refresh the page, list the branches in the drop down -- hello will still not exist because we have yet to push it up.

### 9. Making changes: add (stage) / commit / push
- To push up the new `hello` branch, we can simply push up the branch on its own. It has no changes whatsoever and the file contents look exactly like `main` from which we branched from. But, the creation of a new branch, is, in and of itself, a change. Therefore we can simply push it by running:
    - `git push`
- After running the push command above, you will get the following message: 
    ```
    $ git push
      To push the current branch and set the remote as upstream, use
      git push --set-upstream origin hello
    ```
- This basically means that you need to tell it what branch this local branch will map to in on the remote repository. That is to say --`hello` branch exists locally, but not remotely. So we need to use the `--set-upstream` on our first push to tell it what branch to push up to on the remote. 
- It only makes sense to keep the same name on the remote branch, so let's run the suggested command on our first push:
    ```
    $ git push --set-upstream origin hello
      ...
      * [new branch]      hello -> hello
      branch 'hello' set up to track 'origin/hello'.
    ```
- You can see, amongst other things... it's created a new branch on the remote repo, `origin/hello`. Above it, it has mapped `hello` with (hello) `hello`. The former is the local branch. The latter is the _hello_ branch in the remote world. 
- Now, if you log in to your GitHub UI and inspect the list of branches, you will see that `hello` will be in the list.

### 9. Challenges:

- The following can be done by you. You can use both the information found in this exercise and the steps in the video for Session 1 - to assist you with these challenges. Please aim to complete ALL of them.
    - **Checkout the `main` branch**
    - **Write a new file called `hello.txt` with one line: `hello world`**
    - **Run `git status`**
    - **Add the file `hello.txt` so it is _staged_**
    - **Commit the file with the commit message: `Adding file hello.txt`**
    - **Push the file to the remote `main` branch**
    - **Switch to `hello` branch**
    - **Stretch: Pull in changes from the `main` branch to the current `hello` branch. This should copy the hello.txt file into the `hello` branch as you are pulling from main.**
 
