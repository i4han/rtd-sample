# Git Workflow

## Setup:

1. In Terminal, verify that you have git installed. 
```
which git
```

If the above command doesn't result in a listed directory, [download git](http://git-scm.com/download/mac).

Open the Self Service application on your machine and log in.

On the `Categories` panel on the right hand side, select `Scripts > Make Me an Admin`

Run the git installer.

2. On github, find the repo you want and fork it to your own github account.
```
https://github.com/gopro/some-repo
```

3. Copy the URL for the forked repo on your account.
```
https://github.com/youraccount/some-repo
```

4. In Terminal, create a directory where to store all of your local cloned repos.
```
mkdir repo
```

5. Navigate to that directory and clone your forked repo.
```
cd repo
git clone https://github.com/youraccount/some-repo
```

6. Navigate into the resulting directory.
```
cd some-repo
```

7. Add the original GoPro repo as a remote upstream repo for rebasing.
```
git remote add upstream https://github.com/gopro/some-repo
```

If you run `git remote -v` to list remotes, you should now be able to see both your fork (`origin`) and the original repo (`upstream`).


## Cut a New Branch, Make and Commit Your Edits:
1. Create a new branch for the work you're about to do with `git checkout -b [branch_name]`
1. Open the file you want to edit in the text editor you like. I prefer Sublime. Visual Studio Code offers markdown preview.
1. When you're done editing, save the file.
1. From the repo directory in Terminal, see which files contain changes by typing `git status`.
1. Add those files to your commit with `git add file1.md file2.md file3.md`
1. Make your commit with `git commit`, which will open Vim.
1. Type `i` to enter 'interactive' mode. Type a short commit message that describes the changes you made, like "Removed section on roles." 
1. Press `ESC` to exit 'interactive mode', type `:wq` and hit `Enter` to `write` and `quit`.

## Rebase, Push to Your Fork, and Submit a Pull Request:
1. Run `git pull --rebase upstream master` to rebase from the original repo. This ensures that your local cloned repo captures any changes made in the original since you began working.
1. Push your changes to a new branch on your forked repo on github, with `git push remote [branch_name]`.
1. On Github, submit a Pull Request (PR) from the `[branch_name]` branch of your forked repo to the `Master` branch of the original repo.
1. Ask a teammate to review and merge your PR.