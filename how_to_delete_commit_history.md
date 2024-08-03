
## Objective

Completely delete the commit history of a GitHub repository while maintaining the current source code.

> ⚠️ **Warning**: Completely deleting the commit history of a GitHub repository is not usually recommended. It is a significant action that should be carefully considered, as it will erase all the history of the repository.

## Steps to Delete the Commit History of the Master Branch

1. **Checkout the Repository**

   Navigate to your local repository and create a new orphan branch.

   ```bash
   $ cd TO_LOCAL_GITHUB_REPOSITORY
   $ git checkout --orphan orphan_branch
   ```

   > ✅ Using the Git command, create a new orphan branch (`orphan_branch`). Here, `orphan_branch` represents the name of the new branch.

2. **Add and Commit All Files**

   Add all files and make an initial commit.

   ```bash
   $ git commit -am "Initial commit"
   ```

3. **Delete the Master Branch and Rename Current Branch**

   Delete the master branch and rename the current branch to master.

   ```bash
   $ git branch -D master
   $ git branch -m master
   ```

4. **Force Push to Remote Repository (GitHub)**

   Force push the changes to the remote repository to update it.

   ```bash
   $ git push -f origin master
   ```

   > ✅ With these steps, the commit history of the master branch has been completely cleared.
