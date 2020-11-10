# Getting Started with Git

# Preparation for Meetup

  1. Install the Git software appropriate for your operating system.
  1. Install a code editor.  
     If you have an editor you already use and like, keep using it.  
     Otherwise, these are couple of popular (and free) choices worth checking out:
     - [VS Code][vscode]
  1. Sign up for an account on [GitHub](https://github.com).


## Mac OS X

Install [Homebrew][mac_homebrew].  After you have homebrew installed update to the latest version of Git:

    $ brew install git

Optional tools:

    $ brew install tree
    $ brew install starship

## Linux

Ubuntu/Debian systems:

    $ sudo apt update
    $ sudo apt install -y git

See READMEs of tools like `startship` and `bash-git-prompt` for installation help.
- [Starship][starship_prompt]
- [bash-git-prompt][bash_git_prompt]

## Windows

Download and install [Git for Windows][git_windows] (includes Bash).

# Software Carpentry

The materials exercises in this workshop are heavily influenced by those made freely available by the [Software Carpentry group][sw_carpentry].

Our thanks goes out to them for the course material they produce and the work they do in helping people level up with important tech skills.

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

Git BASH and these exercises are unix-centric, which can be unfamiliar to those new to the command line.  Please ask questions!

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


### Navigating the Command line:

| Key combo     | Effect | 
|---------------|-------------------------|
| UP-ARROW      | edit last command executed |
| CTRL-a        | go to beginning of line |
| CTRL-e        | go to end of line |
| CTRL-w        | delete word *preceding* cursor
| CTRL-u        | delete from cursor to beginning of line |


# Initial Configuration

Check if you have git configured already:

    $ git config --list

If not already configured, add your name and email:

    $ git config --global user.name "Your Name"
    $ git config --global user.email "you@example.com"

If you want to use **VS Code** as the editor for your commit messages:

    $ git config --global user.editor "code -n -w"

Example configurations for other editors [HERE](git_editor).

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


# Lesson 1:  Start Using a Git Repository

Git commands we'll use:
- `git status`
- `git init`
- `git add`
- `git commit`


There are two common ways to set up a git repository (repo) on your local system:
- initialize a new one
- copy one from another location (covered later)

## Follow Along

1. Create a new directory named `git-exercises`
1. Change into this directory  
  `cd git-exercises`
1. Notice that git is not yet tracking this directory:  
   `git status`  
1. Check directory contents:  
   `ls -la`
1. Initialize this as a new repository:  
  `git init`
1. Check the directory contents again:  
  `ls -la`  
  `tree` (optional)
1. Create a new file `hello.py` with some content
1. Check the current status:  
  `git status`
1. Add the recent change using a 2 step process:
    1. Notify git we want to track the changes of this new file:  
  `git add hello.py`
    1. Commit the change using either: 
  `git commit`  
  `git commit -m "log message"`
1. Check the git history using either:  
  `git log`  
  `git log --oneline`


## Excercise 1

1. If you haven't yet done so, create the `git-exercises` directory and initialize as a git repo.
1. Create a file `python.txt` and write a line or two about how you currently use or would like to use Python.
1. Add and commit that file to git.
1. Verify your commit in the git log.







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

    id_ed25519
    id_ed25519.pub
    id_rsa
    id_rsa.pub

If not, create them using `ssh-keygen`:

    $ ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519 -C "EMAIL_USED_WITH_GITHUB"

Copy the *public* key (with `.pub` extension) to your clipboard:

    # use id_rsa.pub instead if you already have it
    $ pbcopy < ~/.ssh/id_ed25519.pub

Add this public key to GitHub: **Settings > SSH and GPG keys**


# Misc.

### Starship configuration

Add the following to your `~/.bashrc`

```bash
# delegate to starship for bash prompt config
#   https://github.com/starship/starship
if [[ -n "$(command -v starship)" ]]; then
  eval "$(starship init bash)"
  eval "$(starship completions bash)"
else
  echo "Unable to configure prompt, 'starship' not found."
fi
```



[sw_carpentry]: https://software-carpentry.org/
[git_exercises]: http://swcarpentry.github.io/git-novice/ 
[podcast]: https://talkpython.fm/episodes/show/93/spreading-python-through-the-sciences-with-software-carpentry
[vscode]: https://code.visualstudio.com/
[git_windows]: https://gitforwindows.org/
[mac_homebrew]: https://brew.sh/
[sample_repo]: https://github.com/PDXPythonPirates/wordplay
[git_bash_contrib]: https://github.com/git/git/tree/master/contrib/completion
[starship_prompt]: https://github.com/starship/starship
[bash_git_prompt]: https://github.com/magicmonty/bash-git-prompt
