# Motivation

- GUI clients suck
- GUI clients are incomplete
- GUI clients aren't always available (think RStudio Server)

# Development workflow

0. Empty status, all tests green
1. Hack
2. Add, commit
3. If interesting changes left, go to 2
4. Clean up
5. Go to 0

Mental model: Sequence of commits, staging area.

## The shell

- `git sh`
- `bash` + omit `git`
    - Shortcuts for frequently used commands
- Ctrl + C
- Cursor keys, Ctrl + R
- Ctrl + D

## The basic commands, revamped

- `status` / `diff`
- `add` / `reset`
- `commit -m "message"`
- `checkout` / `clean`
- `log`, `log --patch`
- `blame`

# Interactive commands

## Using `less`

- Scrolling
- Home, End
- Search with `/`

## Getting help

- `git help`

## Interactive commands

- `commit` without `-m`
- `add -p` with editing

## Using `vi`

- Navigation
- Insertion/deletion
- Deletion of whole lines
- Quitting

# Feature branch workflow

0. Empty status, all tests green
1. Switch to new branch
2. Develop
3. Review
4. Merge to `master`
5. Go to 0

## Branching and merging

- `branch`
- `checkout -b <branch>`
- `branch <branch>`
- `reset --hard`
- `checkout <branch>`
- `merge <branch>`
- `log`, `log --first-parent`
- `branch -d`
- `reset`

Mental model: DAG of commits, branches are pointers.

## Conflict resolution

- `merge --abort`
- `diff`, `diff --ours`, `diff --theirs`
- `merge -X`, `checkout --ours`, `checkout --theirs`

Mental model: overlapping patches.

## Navigation, refspecs

- `HEAD`
- `HEAD^`
- sha1
- `checkout <ref>`
- `ref..ref`
- `ref...ref`
- `diff <refspec>`

Mental model: Naming, navigation, exclusion.

## Rebasing

- `rebase`
- `rebase --interactive`
- `commit --fixup`

Mental model: rewrite history.

# Bisection

- `bisect`

Mental model: needle and haystack.

# Initialization

- `init`
- `commit --allow-empty`

# Resources

- http://rogerdudler.github.io/git-guide/
