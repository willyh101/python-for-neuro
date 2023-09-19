## Episode 1 - Getting Started

These instructions are for installing Python on a Mac. If you are using Windows it should be similar, but you'll need to read the docs in more detail. Unless you REALLY want windows for some reason, install Ubuntu (you can install it alongside Windows and boot Windows if you ever need it). If you are already using Linux, you probably already know what you are doing...

### Installing Python in 2023

The best way to install Python now is to via a variant of the conda/Anaconda package manager, [mamba](https://mamba.readthedocs.io/en/latest/mamba-installation.html). This is a faster version of conda and helps significantly with installing into complicated environments with a lot of dependencies. Any command you see online that uses `conda` can be replaced with `mamba` and it should work the same, just faster. **The rest of these instructions assume you are using a Mac.** Ubuntu will be very similar except generally you'll just use `apt` instead of `brew` to install things. Windows is pretty different-- talk to me about it.

Step 0: If you do not have [homebrew](https://brew.sh) installed, install it with the following command in a terminal window:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Close your terminal window and open a new one. Run `brew doctor`. If you get the error `zsh: command not found: brew` then you need to add homebrew to your path. Run the following command to add brew to your PATH:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Homebrew is basically a really easy way to install software on a Mac. It's like the app store, but for the command line.

Next, install mamba:

```bash
brew install --cask mambaforge
```

Then run this to setup your shell (aka command line, aka terminal) to use mamba:

```bash
conda init "$(basename "${SHELL}")"
```

Then restart your terminal window. This *should* be all you need to get started. Test it!
    
```bash
mamba --version
```

Assuming that worked, create an environment for our minicourse. You can create as many environments as you want, and it's good practice to keep them separate. I have one environment for my analysis and keep it seperate from any random things I install. Scientific packages can have a bunch of weird dependencies and you run the risk of downgrading or worse breaking installations of critical packages when you start adding too much stuff in. 

This will create a new environment called `neuro` with Python installed and activate it:

```bash
mamba create -n neuro python
mamba activate neuro
```

Whenever you want to use this environment, you'll need to activate it. You can deactivate it with `mamba deactivate`.

*** Note: If using `mamba activate` doesn't work, try `conda activate` instead. This should be the only command where you have to use conda instead of mamba.

Then install some basic packages we'll need:

```bash
mamba install numpy scipy matplotlib jupyterlab notebook pandas
```

There are some additional python packages that we need that aren't available via conda. We'll install those with pip. Pip is the traditional python package manager. We often use mamba/conda instead because it's easier to install packages that have a lot of dependencies or require non-python libraries (aka scientific ones).

```bash
pip install scanimage-tiff-reader tifffile
```

### Other helpful things to do now
- Install [VSCode](https://code.visualstudio.com), also install the python extension
- git is critical but probably already installed. If not, install it with `brew install git`
- Maybe you also want [GitHub Desktop](https://desktop.github.com) for visualizing git repos
- Create a GitHub account if you haven't already (not critical now, but will be useful later)
- Install [ohmyzsh](https://ohmyz.sh). This is totally optional, but it makes the terminal prettier and a lot nicer to use.

### Other command line usefulness

- `ls` - list files in the current directory
- `cd` - change directory
- `pwd` - print working directory
- `mkdir` - make a new directory
- `nano` - a simple text editor
- `touch` - create a new file

### Helpful aliases

Aliases are like shortcuts for otherwise hard to remember but often used commands. I recommend creating a file called `.aliases` in your home directory and adding the following aliases to it. 

```bash
cd ~ # this takes you to your home directory (aka /Users/[your_username])
touch .aliases
nano .aliases

# technically you can use any text editor you want, but nano is the easiest to use
# also, all of the above can be shortened to:
nano ~/.aliases
```

- `alias ll="ls -lhAF"` - list files in the current directory with more information
- `alias la="ls -A"` - list all files in the current directory, including hidden ones
- `alias l="ls -CF"` - list files in the current directory in columns
- `alias mkcd='fn(){ mkdir -p "$1"; cd "$1" }; fn '` - make a directory and cd into it in one command. Usage: `mkcd [my_new_dir]`
- `alias reload='source ~/.zshrc'` - reload your zsh config file. Useful if you add new aliases or functions and want to use them without restarting your terminal.

Then add the following line to your `.zshrc` file (also in your home directory) to load the aliases file when you open a new terminal window:

```bash
if [ -f ~/.aliases ]; then
    . ~/.aliases
fi
```

### Set up a folder for this minicourse
[to be continued...]