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

# The shell

- `git sh`
- Shortcuts for frequently used commands
- Ctrl + C
- Cursor keys, Ctrl + R
- Ctrl + D

# The basic commands, revamped

- `status` / `diff`
- `add` / `reset`
- `commit`
- `checkout` / `clean`
- `log`

# Using `less`

- Scrolling
- Home, End
- Search with `/`

# Getting help

- `git help`

# Interactive commands

- `commit` without `-m`
- `add -p` with editing

# Using `vi`

- Navigation
- Insertion/deletion
- Deletion of whole lines
- Quitting

# Branching and merging

- `checkout -b`
- `branch`, `reset --hard`
- `checkout`
- `merge`
- `log`, `log --first-parent`

Mental model: DAG of commits, branches are pointers.

# Conflict resolution

- `merge --abort`
- `diff`, `diff --ours`, `diff --theirs`
- `merge -X`, `checkout --ours`, `checkout --theirs`

Mental model: overlapping patches.

# Rebasing

- `rebase`
- `rebase --interactive`
- `commit --fixup`

Mental model: rewrite history:

# Bisection

- `bisect`

Mental model: needle and haystack.

# Initialization

- `init`
- `commit --allow-empty`

# Resources

- http://rogerdudler.github.io/git-guide/
