# Getting Started with Git


# Key Concepts Tonight

- Git repository
- Commit
- Commit hash
- Symbolic names (branch names, tags, `HEAD`)
- Working area / staging (index) / repository
- Git != GitHub (or GitLab or BitBucket)

# References

- [Main Git site][git_scm]
- [Pirates Git Resources](https://www.pythonpirates.org/resources/#git-and-github)
- [Git terms][sw_carpentry_git_terms]
- [Git reference][sw_carpentry_git_ref]

# Software Carpentry

The materials exercises in this workshop are heavily influenced by those made freely available by the [Software Carpentry group][sw_carpentry].

Our thanks goes out to them for the course materials they produce and the work they do in helping people level up with important tech skills.

- [Version Control with Git][git_exercises] exercises
- [Talk Python #93][podcast] - SW Carpentry is the show topic


# Preparation for Meetup

  1. Install the Git software appropriate for your operating system.
  1. Install a code editor.  
     If you have an editor you already use and like, keep using it.  
     Otherwise, [VS Code][vscode] is a popular option.
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


# BASH Usage

Git BASH and these exercises are unix-centric, which can be unfamiliar to those new to the command line.  No worries, we're here to help.  Please ask questions!

A few commands and directory shortcuts:

    ls               list directory contents
    cd <path>        change directory to <path>
    cd -             takes you back to your previous directory
    mkdir <dir>      make a new directory
    mv <src> <dest>  move/rename a file or directory
    cat <file>       print contents of a file
    less <file>      prints contents of file, one page at a time
                     use 'q' to exit

    Shorthand
    ~                shorthand for home directory (same as $HOME)
    .                the current directory
    ..               the parent directory



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

**Example configurations for other editors can be found [HERE][git_editor].**

Adding a few aliases can reduce some typing:

    $ git config --global alias.stat status
    $ git config --global alias.s status
    $ git config --global alias.co checkout
    $ git config --global alias.lol  "log --oneline --graph --decorate"

## Windows

Additional config for Windows users:

    $ git config --global credential.helper manager

    # Confirm this is still recommended
    $ git config --global core.autocrlf true

    # Otherwise use standard hands-off policy ('input' for middle ground)
    $ git config --global core.autocrlf false


# Lesson 1:  Making Commits

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
1. Create a file `python.txt` and write a line or two about how you currently use Python.
1. Add and commit that file to git.
1. Create a nested directory within this repo `resources`
    1. Add two files under resources `a.txt` and `b.txt`
    1. Add some random content to each file, whatever you like.
1. Register the *directory* with `git add`:  
  `git add resources`
1. Notice how both files were picked up for add with the next commit:
  `git status`
1. Commit the new files.
1. Verify your commits in the git log.


# Lesson 2: Branching


# Lesson 3: Ignoring Files


# Lesson 4: GitHub Set Up

Fork the [Wordplay repo][sample_repo] so you have a copy under your own account.

Clone the repo to your local machine.
- Windows: use the **HTTPS** URL
- Mac/*nix: use the **SSH** URL

    $ git clone <REPO_URL>

## Mac and other *nix

Check if you already have an SSH key pair:

    $ ls -la ~/.ssh

    id_ed25519
    id_ed25519.pub
    id_rsa
    id_rsa.pub

If not, create them using `ssh-keygen`:

    $ ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519 -C "EMAIL_USED_WITH_GITHUB"

Note: you may not want your email to be public.  The GitHub *setting* links to information about using a private email address [HERE][github_private_email].

Copy the *public* key (with `.pub` extension) to your clipboard:

    # use id_rsa.pub instead if you already have it
    $ pbcopy < ~/.ssh/id_ed25519.pub

Add this public key to GitHub: **Settings > SSH and GPG keys**


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




[git_scm]: https://git-scm.com/
[sw_carpentry]: https://software-carpentry.org/
[git_exercises]: http://swcarpentry.github.io/git-novice/ 
[sw_carpentry_git_ref]: http://swcarpentry.github.io/git-novice/reference 
[sw_carpentry_git_terms]: http://swcarpentry.github.io/git-novice/reference#commit
[podcast]: https://talkpython.fm/episodes/show/93/spreading-python-through-the-sciences-with-software-carpentry
[vscode]: https://code.visualstudio.com/
[git_editor]: http://swcarpentry.github.io/git-novice/02-setup/index.html
[git_windows]: https://gitforwindows.org/
[mac_homebrew]: https://brew.sh/
[sample_repo]: https://github.com/PDXPythonPirates/wordplay
[git_bash_contrib]: https://github.com/git/git/tree/master/contrib/completion
[starship_prompt]: https://github.com/starship/starship
[bash_git_prompt]: https://github.com/magicmonty/bash-git-prompt
[github_private_email]: https://github.com/settings/emails
