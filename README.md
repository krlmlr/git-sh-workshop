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
    
6. Take a look at the log.

    - `l`


7. Start implementing a `show_pink()` function, then throw it away.

    - `coa`

7. Experiment with throwing away selective changes.

    - `cop`

8. Create a new file, save it, then throw it away.

    - `clean -df`

9. Create a new file, commit it.

10. Remove this file, commit this change.

    - `a`

### B: Interactive commands

1. Add a `show_yellow()` function at the top, and a `show_cyan()` function to the bottom of `functions.R`, and calls to `script.R`. Commit these changes as atomic units, edit the commit message in `vi`.

    - `ap`, `ci`

2. Take a look at the detailed log. Scroll and search.

    - `lp`, cursor keys, `/`

### C: Branching

1. Create three branches.
