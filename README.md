# git-sh-workshop

## rstudio.cloud instance

- https://rstudio.cloud/project/143049
- Make sure to click "Save as copy" (red icon top right)

## Exercises

Restart all exercises with:

```sh
git checkout .
git clean -fd
git reset --hard origin/master
```

### A: Basic commands

1. Run `script.R`. What does it show?
    - Ctrl + Shift + Enter or Cmd + Shift + Enter

2. Switch to the terminal, start `git sh`
    - Alt + Shift + R, `git sh`

3. Make sure that you have a clean working copy.
    - `s`

4. Add a `show_blue()` function, and a call to that function in `script.R`. Inspect the changes.
    - `d`

5. Commit both changes as an atomic unit.
    - `aa`, `s`, `dc` `cim`
    
6. Add a comment to your code. Commit without changing the commit message.
    - `ciao`
    
7. Take a look at the log.
    - `l`, `lp`

8. Start implementing a `show_pink()` function, then throw it away.
    - `coa`

9. Experiment with throwing away selective changes.
    - `cop`

10. Create a new file, save it, then throw it away.
    - `clean -df`

11. Create a new file, commit it.
    - `a`

12. Remove this file, commit this change.
    - `a`

### B: Interactive commands

1. Add a `show_yellow()` function at the top, and a `show_cyan()` function to the bottom of `functions.R`, and calls to `script.R`. Commit these changes as atomic units, edit the commit message (and perhaps the patch) in `vi`.
    - `ap`, `ci`

2. Amend the commit message.
    - `cia`

3. Take a look at the detailed log. Scroll and search.
    - `lp`, cursor keys, `/`

4. Look up help for the `checkout` command. What did the `-p` switch do again?
    - `git help ...`

### C: Branching and merging

1. Create a branch `f-magenta`, implement a `show_magenta()` function and a call to that function. List your branches.
    - `cob`, `b`

1. Adapt `show_cyan()` to call `glue(inverse(cyan(...)))` instead of `glue(cyan(...))`. Commit. Because you wanted to do it on a new `f-cyan-inverse` branch (instead of `f-magenta`), you need to switch retroactively.
    - `b <branch>`, `reset --hard`, `co <branch>`

1. Create a branch `f-cyan-underline` from `master`, adapt `show_cyan()` to call `glue(underline(cyan(...)))` instead of `glue(cyan(...))`.
    - `cob master`

1. Visualize all branches.
    - `la`

1. Merge `f-magenta` into `master`.
    - `co`, `m`

1. Merge `f-cyan-inverse` into `master` without editing the commit message.
    - `mo`

1. List the merges without the details of the individual branches.
    - `lf`

1. Visualize the differences from each merge.
    - `lfp`

1. Move the head of `master` to `f-magenta`. Explain. Move it back.
    - `reset <branch>`

1. Delete the branches that you have merged successfully. Try deleting the `f-cyan-underline` branch.
    - `bm`, `b -d`

1. Restore the branches that you just deleted.
    - `b <branch> <ref>`

### D: Conflict resolution

1. Try merging `f-cyan-underline` into `master`. Abort the merge.
    - `mo`, `ma`

1. Switch to new a backup of the `f-cyan-underline` branch.
    - `cob`

1. Try merging `master` into the new branch. Inspect.
    - `co`, `mo`, `s`, `dc`, `conflicts`, `do`, `dt`

1. Resolve the conflict by combining the changes from the conflicting branches in `script.R`. Do not add or commit yet -- inspect beforehand. Make sure no conflict markers like `<<<<<<<` remain in the file.
    - `s`, `d`

1. Commit using the default message.
    - `cio`

1. Switch to new a backup of the `f-cyan-underline` branch.
    - `cob`

1. Try merging `master` into the new branch. Inspect. How did Git resolve the conflict?
    - `co`, `mo`, `s`, `dc`, `conflicts`, `do`, `dt`

1. Switch to new a backup of the `f-cyan-underline` branch.
    - `cob`

1. Try merging `master` into the new branch, keeping the changes of the new branch. Inspect.
    - `mo -X ours`

1. Switch to new a backup of the `f-cyan-underline` branch.
    - `cob`

1. Try merging `master` into the new branch, keeping the changes of `master`. Inspect.
    - `mo -X theirs`

1. Switch to `master`, try merging the original `f-cyan-underline` branch. What happens?
    - `co`, `mo`

1. Abort the merge. Merge one of the branches where you successfully resolved the conflict into `master`. Explain.
    - `ma`, `mo`, `la`

### E: Refspecs

1. Check out the `f-magenta` branch again. What happens?
    - `co`

1. Check out the parent of the `f-magenta` branch. What happens?
    - `co`, `l`

1. Use the log to find the SHA of an interesting commit, check it out. Explain.
    - `l`, `co`

1. Switch to `master`, compare with the `f-magenta` branch.
    - `d <ref>`

1. Compare the `f-cyan-inverse` and `f-cyan-underline` branches.
    - `d <ref>..<ref>`

1. What's new in `f-cyan-inverse`, compared to `f-cyan-underline`?
    - `d <ref>...<ref>`

### F: Rebasing

1. Branch off of an earlier revision of `master` that don't include `f-magenta` and `f-cyan-***` yet.
    - `l`, `cob <branch> <ref>`

1. Rebase `f-magenta` onto the new branch. Explain.
    - `co`, `r <branch>`

1. Move the new branch. Reset the tip of the new branch to the rebased `f-magenta`.
    - `co`, `reset <branch>`

1. Rebase `f-cyan-inverse` onto the new branch. Explain.
    - `co`, `r <branch>`

1. Move the new branch. Reset the tip of the new branch to the rebased `f-cyan-inverse`.
    - `co`, `reset <branch>`

1. Rebase `f-cyan-underline` onto the new branch. Explain.
    - `co`, `r <branch>`
    
1. Abort the rebase. Explain.
    - `ra`

1. Rebase `f-cyan-underline` onto the new branch, again.
    - `r <branch>`
    
1. Resolve the conflict, continue the rebase. 
    - `rc`

1. Move the new branch. Reset the tip of the new branch to the rebased `f-cyan-underline`.
    - `co`, `reset <branch>`

1. Inspect the log. How is it different from the merging exercise?
    - `l`

### G: Bisecting

Task: Find the commit that introduced that magenta output function.

1. Set `master` as "bad" revision, agree to start bisection.
    - `bisect bad <branch>`

1. Find an earlier revision of `master` that don't include `f-magenta` yet. Set that earlier revision as "good".
    - `l`, `bisect good <ref>`

1. Do not look at the code. Run `script.R` to check if there is magenta output. If yes, it's a "bad" revision, otherwise a "good" one.
    - `bisect bad`, `bisect good`

1. Rinse and repeat, until you find your bad commit. Double-check that this is indeed the change that introduces magenta output.
    - `show <ref>`

1. Finish bisection.
    - `bisect reset`
