# Getting Started with Git

# Preparation for Meetup

  1. Install the Git software appropriate for your operating system.
  1. Install a code editor.  
     If you have an editor you already use and like, keep using it.  
     Otherwise, these are couple of popular (and free) choices worth checking out:
     - [VS Code][vscode]
     - [Atom][atom]
  1. Sign up for an account on [GitHub](https://github.com).


## Windows

Download and install [Git for Windows][git_windows] (includes Bash).

## Mac OS X

Install [Homebrew][mac_homebrew].  After you have homebrew installed update to the latest version of Git:

    $ brew install git

## Linux

I trust you already know how to install software on your linux system :)


# Git Excercises

Our plan is to follow some Git exercises courtesy of the [Software Carpentry][sw_carpentry] group. 

- [Version Control with Git][git_exercises] exercises
- [Talk Python #93][podcast] - SW Carpentry is the show topic


# Key Concepts Tonight

- Git repository
- Commit
- Commit hash
- Symbolic names (branch names, tags, `HEAD`)
- Working area / staging (index) / repository
- Git != GitHub (or GitLab or BitBucket)


## Note

Git BASH and these exercises are unix-centric, which can be unfamiliar to Windows users.  The exercise does a decent job of explaining the commands used, but you may still have questions.  Please ask!

A few commands and directory shortcuts:

    ls               command to list directory contents
    cd <path>        command to "change directory"
    mkdir <dir>      command to make a new directory
    mv <src> <dest>  command to move/rename a file or directory
    cat <file>       command to print contents of a file

    ~                shorthand for home directory (same as $HOME)
    .                the current directory
    ..               the parent directory

    cd -             takes you back to your previous directory

# Additional Git Configuration

Configure your name and email:

    $ git config --global user.name "Your Name"
    $ git config --global user.email "you@example.com"

Configure a global `.gitignore`:

    $ git config --global core.excludesfile "~/.gitignore_global"

If you want to use **VS Code** as the editor for your commit messages:

    $ git config --global user.editor "code -n -w"


I recommend adding a few aliases to reduce some typing:

    $ git config --global alias.stat status
    $ git config --global alias.co checkout
    $ git config --global alias.lol  "log --oneline --graph --decorate"

## Windows

Additional config for Windows users:

    $ git config --global credential.helper manager

    # Confirm this is still recommended
    $ git config --global core.autocrlf true

    # Otherwise use standard hands-off policy ('input' for middle ground)
    $ git config --global core.autocrlf false


# GitHub Setup

Fork the [Wordplay repo][sample_repo] so you have a copy under your own account.

Clone the repo to your local machine.
- Windows: use the **HTTPS** URL
- Mac/*nix: use the **SSH** URL

    $ git clone <REPO_URL>

## Windows

Make sure you configured:  
`git config --global credential.helper manager`

Create a Personal Access Token (PAT) using the GitHub website.  
**Settings > Developer settings > Personal access tokens**

> *KEEP THIS BROWSER TAB OPEN!*

Clone a repo you have under your user account in GitHub.
You can either create a new one or **fork** an existing one.  
> We will demonstrate how to create a **fork**.

Execute a `git push` to a cloned repo.  When prompted, enter:
- your github username
- your new **Personal Access Token** for the password


## Mac and other *nix

Check if you already have an SSH key pair:

    $ ls -la ~/.ssh

    id_rsa
    id_rsa.pub

If not, create them using `ssh-keygen`:

    $ ssh-keygen -t rsa -b 4096 -C "EMAIL_USED_WITH_GITHUB"

Copy the *public* key (with `.pub` extension) to your clipboard:

    $ pbcopy < ~/.ssh/id_rda.pub

Add this public key to GitHub: **Settings > SSH and GPG keys**





[sw_carpentry]: https://software-carpentry.org/
[git_exercises]: http://swcarpentry.github.io/git-novice/ 
[podcast]: https://talkpython.fm/episodes/show/93/spreading-python-through-the-sciences-with-software-carpentry
[vscode]: https://code.visualstudio.com/
[atom]: https://atom.io/
[git_windows]: https://gitforwindows.org/
[mac_homebrew]: https://brew.sh/
[sample_repo]: https://github.com/PDXPythonPirates/wordplay
[git_bash_contrib]: https://github.com/git/git/tree/master/contrib/completion

