<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Install git](#install-git)
- [Create GitHub account](#create-github-account)
- [Configure Git](#configure-git)
- [Install Fork](#install-fork)
- [Install Visual Studio Code](#install-visual-studio-code)
- [Set VS Code as default editor](#set-vs-code-as-default-editor)
- [Git alias for generating commits](#git-alias-for-generating-commits)
- [Git alias for better git history](#git-alias-for-better-git-history)
- [Git alias for more detailed git history](#git-alias-for-more-detailed-git-history)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

You're going to install a bunch of things!

# Install git

Follow [these instructions](./installGit.md) if you haven't already to install git.

# Create GitHub account

If you haven't already, [create a GitHub account](http://github.com/) on the public site.

# Configure Git

You'll need to tell git who you are, so it can attribute commits to you as the author. **Generally you use your real name and email associated with GitHub**, though you can actually put whatever you want.

Paste these two lines into your bash shell, substituting the values as appropriate.

```bash
$ git config --global user.name "Your Name"
$ git config --global user.email "your@email.com"
```

You can then confirm they're configured like this:

```
$ git config --global user.name
Andrew Smith

$ git config --global user.email
andrewsmith@alumni.stanford.edu
```

This is a **local configuration**. It does not create a GitHub account for you. It is only used by git to identify who is creating commits, and adding author information about it.

# Install Fork

We will work with [Fork](https://git-fork.com/), the best git GUI app on the market. There are other free options, but they're not as good and less effective for learning purposes.

It will ask if you want to connect to any accounts. You can connect to your GitHub account if you want, or not, it's just a convenience thing to display your GitHub repositories.

# Install Visual Studio Code

Download it [here](https://code.visualstudio.com/).

# Set VS Code as default editor

You can use [Visual Studio Code](https://code.visualstudio.com/) as the default editor in your shell.

Inside VS Code, open the Command Palette (CMD + Shift + P or Ctrl + Shift + P) and search for "Shell Command: Install 'code' command in PATH", follow that step. **If you're on Windows, this is done for you automatically.**

Then next command you should run depending on which shell you run.

**If your terminal prompt starts with a %**

<details><summary>Click here</summary>

> It might look something [like this](https://i.stack.imgur.com/bUR9P.png).
>
> Run this command in your shell:
>
> ```bash
> % echo 'export EDITOR="code -w"' >> ~/.zshrc
> ```
>
> Then open a NEW shell and check that it's been set correctly:
>
> ```bash
> % echo $EDITOR
> 
> should print out: code -w
> ```
</details>

**If your terminal prompt starts with a $**

<details><summary>Click here</summary>

> It might look something [like this](https://miro.medium.com/max/1960/0*jdx5-Ww6NH3ozn0Z.png).
>
> Run this command in your shell:
>
> ```bash
> echo 'export EDITOR="code -w"' >> ~/.bash_profile
> ```
>
> Then open a NEW shell and check that it's been set correctly:
>
> ```bash
> $ echo $EDITOR
> 
> should print out: code -w
> ```
</details>

# Git alias for generating commits

Eventually you'll want to be able to quickly generate commits. When that time comes, these tools can be handy.

Just copy each line individually and paste them into your shell.

```
$ git config --global alias.commitrand '!f() { echo asdf$1 > $1.txt && git add . && git commit -m "Add $1.txt."; }; f'
```

**There is no output in return.**

Verify it's set up correctly:

```bash
$ git config --global alias.commitrand

# you should see:
# !f() { echo asdf$1 > $1.txt && git add . && git commit -m "Add $1.txt."; }; f
```

Sample usage:

```bash
$ git commitrand 3  # creates a file 3.txt and creates a commit
                    # with commit message "Add 3.txt."
```

# Git alias for better git history

This will display a clean, visually friendly git log, showing all the branches. Copy and paste this command into your shell.

```bash
$ git config --global alias.l 'log --graph --decorate --pretty=oneline --abbrev-commit --all'
```

**There is no output in return.**

Verify it's set up correctly:

```bash
$ git config --global alias.l

# you should see:
# log --graph --decorate --pretty=oneline --abbrev-commit --all
```

Then use it with:

```bash
$ git l
```

# Git alias for more detailed git history

And this is an expanded form, showing dates and author name. Copy and paste...

```bash
$ git config --global alias.hist "log --pretty=format:'%C(yellow)%h%Creset %Cgreen%ad%Creset | %s%C(magenta)%d%Creset [%Cblue%an%Creset]' --graph --date=short --decorate"
```

**There is no output in return.**

Verify it's set up correctly:

```bash
$ git config --global alias.hist

# you should see:
# log --pretty=format:'%C(yellow)%h%Creset %Cgreen%ad%Creset | %s%C(magenta)%d%Creset [%Cblue%an%Creset]' --graph --date=short --decorate
```

And then use:

```bash
$ git hist
```
