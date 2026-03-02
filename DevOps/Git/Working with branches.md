Git uses branches to "branch" your code into different development paths, you can fork your code using the branch command, modify one branch while the other stays the same, or modified differently. Then you can merge your changes into a single branch or keep your changes separated.

For branching to work you need at least 1 existing branch, adding an committing your first change will add the `master` branch, and from there you can branch into another branch

```bash
git branch development
```

This will create a new Branch named `development`.

You can list all the branches 

```bash
> git branch
  development
* master
```

The `*` denotes the current branch. To change the current branch run ` git checkout` or `git switch`.

```bash
> git switch development
Switched to branch 'development'

> git branch
* development
  master
```

When you are working on a specific branch and would like to see stages and uncommitted files along with the current branch, run

```bash
> git status
On branch master                                                                      
Changes to be committed:                                                              
  (use "git restore --staged ..." to unstage)                                         
        new file:   index.html
```