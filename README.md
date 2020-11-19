Most of the repos here are meant to simplify and enhance the developer
experience, especially as it relates to working in a command-line environment,
using common command-line tools, modifying source code, setting up developer
environments, building flexible custom tools, working with data, building
prototypes, exploring open source projects, and learning.

When I first learned UNIX fundamentals and shell scripting in 2004, I was also
exposed to the [vim text editor](https://www.vim.org/about.php) and became
hooked on the efficient ways of navigating and editing text. I tend to use
vim-keybindings in other programs wherever they are available.

### Python

The [Learning Python 3
gist](https://gist.github.com/kenjyco/69eeb503125035f21a9d) **(28 stars as of
11/17/20)** includes an
interactive notebook file and sections on:

- Python objects, basic types, and variables
- Basic operators
- Basic containers
- Accessing data in containers
- Python built-in functions and callables
- Python object attributes (methods and properties)
- Some methods on string objects
- Some methods on list objects
- Some methods on set objects
- Some methods on dict objects
- Positional arguments and keyword arguments to callables
- *and several more sections with empty/incomplete content*
    - this guide was created while introducing middle school students to Python
      and Linux in an afterschool setting
    - we never got past this part, so I didn't flesh out the rest of the guide

The [kenjyco python packages
gist](https://gist.github.com/kenjyco/cb601fb3075a724c9e2951f164d1d4d8) has
information about how the various Python packages in this account are connected
to each other, the console-scripts that are provided, and the most used features
of each.

- fundamental/core packages
    - [bg-helper](https://github.com/kenjyco/bg-helper)
    - [chloop](https://github.com/kenjyco/chloop)
    - [dt-helper](https://github.com/kenjyco/dt-helper)
    - [fs-helper](https://github.com/kenjyco/fs-helper)
    - [input-helper](https://github.com/kenjyco/input-helper)
    - [settings-helper](https://github.com/kenjyco/settings-helper)
    - [webclient-helper](https://github.com/kenjyco/webclient-helper)
- data packages
    - [mongo-helper](https://github.com/kenjyco/mongo-helper)
    - [redis-helper](https://github.com/kenjyco/redis-helper)
    - [sql-helper](https://github.com/kenjyco/sql-helper)
- audio/video packages
    - [mocp](https://github.com/kenjyco/mocp)
    - [mocp-cli](https://github.com/kenjyco/mocp-cli)
    - [yt-helper](https://github.com/kenjyco/yt-helper)
    - [vlc-helper](https://github.com/kenjyco/vlc-helper)
- misc packages
    - [aws-info-helper](https://github.com/kenjyco/aws-info-helper)
    - [beu](https://github.com/kenjyco/beu)
    - [easy-workflow-manager](https://github.com/kenjyco/easy-workflow-manager)
    - [jira-helper](https://github.com/kenjyco/jira-helper)
    - [parse-helper](https://github.com/kenjyco/parse-helper)

### Shell/Setup

- the [base](https://github.com/kenjyco/base) repo is an easy way to install
  essential libs/programs for opensource exploration and development 
    - the [install.sh](https://github.com/kenjyco/base/blob/master/install.sh)
      file can be sourced to install packages, create 3 symbolic links in
      `$HOME` and ensure tab-completion is setup for `git` and `docker`
        - if vim or tmux are installed to the system, but there is no `~/.vimrc`
          or `~/.tmux.conf`, the dotfiles repo (below) will be cloned and setup
          as well
    - the [commands.sh](https://github.com/kenjyco/base/blob/master/commands.sh)
      file (one of the symbolic links created points to this) contains many
      conditionally defined shell functions and aliases that should work on
      Ubuntu/Mac in either Bash/Zsh
        - the install.sh updates existing `~/{.bashrc,.zshrc}` file to source
          commands.sh if the symbolic link exists
    - the [bin](https://github.com/kenjyco/base/tree/master/bin) directory
      contains many useful shell scripts (the 3rd symbolic link created)
    - the [Usage section of
      README](https://github.com/kenjyco/base/blob/master/README.md#usage)
      contains  examples on using some of the most useful things in
      `commands.sh` and `bin`
    - the [HISTORY.md](https://github.com/kenjyco/base/blob/master/HISTORY.md)
      file has many organized links and short summaries to Wikipedia articles
      related to programming languages, companies/organizations, important
      terms, and people
    - the [repos.sh](https://github.com/kenjyco/base/blob/master/repos.sh) file
      has links to MANY popular/important git repositories across many
      programming languages
        - they are grouped in Bash arrays and there is a `clone-opensource`
          shell func that will clone all of these locally into grouped
          sub-directories (this takes a LONG time to run and a significant
          amount of space on disk)
        - info as of 11/17/20 at commit
          [02f0d43](https://github.com/kenjyco/base/blob/02f0d432230a710fd8cdc0fe7da80d2c7e835129/repos.sh)

            ```
            opensource % du -sch *
            89M     algorithms
            174M    books
            39G     c
            6.9G    c++
            2.5G    dart
            179M    dockerfiles
            2.6G    docs
            197M    elixir
            740M    erlang
            11G     go
            85M     haskell
            7.4G    java
            8.2G    javascript
            1.6M    jupyter
            40M     lua
            18G     python
            132M    python_async
            3.2G    ruby
            4.6G    rust
            177M    sass
            713M    scala
            192M    shell
            26M     swift
            9.5G    typescript
            2.3M    vimscript
            114G    total

            opensource % repos-dirs
            168 /home/ken/repos/opensource/python
             80 /home/ken/repos/opensource/javascript
             77 /home/ken/repos/opensource/docs
             67 /home/ken/repos/opensource/c
             54 /home/ken/repos/opensource/go
             34 /home/ken/repos/opensource/typescript
             30 /home/ken/repos/opensource/ruby
             27 /home/ken/repos/opensource/java
             19 /home/ken/repos/opensource/shell
             17 /home/ken/repos/opensource/c++
             12 /home/ken/repos/opensource/elixir
             12 /home/ken/repos/opensource/python_async
              9 /home/ken/repos/opensource/books
              9 /home/ken/repos/opensource/rust
              8 /home/ken/repos/opensource/algorithms
              7 /home/ken/repos/opensource/dart
              4 /home/ken/repos/opensource/dockerfiles
              3 /home/ken/repos/opensource/erlang
              3 /home/ken/repos/opensource/lua
              3 /home/ken/repos/opensource/scala
              2 /home/ken/repos/opensource/vimscript
              1 /home/ken/repos/opensource/haskell
              1 /home/ken/repos/opensource/jupyter
              1 /home/ken/repos/opensource/sass
              1 /home/ken/repos/opensource/swift
            ```
        - the benefit of having so many popular repositories cloned locally in
          an organized manner allows exploring code, project layout, patterns,
          and examples that exist in them
- the [dotfiles](https://github.com/kenjyco/dotfiles) repo is where I have Vim,
  tmux, Git, and X/awesome-wm settings (for Linux and Mac)
    - there is a
      [setup.bash](https://github.com/kenjyco/dotfiles/blob/master/setup.bash)
      script that will backup original dotfiles and create symbolic links in
      `$HOME` to the settings in this repo
    - there is also a
      [Background.md](https://github.com/kenjyco/dotfiles/blob/master/Background.md)
      doc that explains a little bit about Bash, Zsh, and Vim
    - before May 2020, there were also a lot of shell aliases, functions, and
      scripts included; many of those are now in the `base` repo, but you can
      find the original files here:
        - old [bin](https://github.com/kenjyco/dotfiles/tree/full/bin)
        - old [shell](https://github.com/kenjyco/dotfiles/tree/full/shell)
    - also see the first commit from Dec 2014
      [8ab93fc](https://github.com/kenjyco/dotfiles/commit/8ab93fcbef3fbc8e1bf64e5eb7826f533c29ad8c)
- the semi-depricated [x200](https://github.com/kenjyco/x200) repo is where I
  stored setup scripts and instructions for fresh Ubuntu Minimal (14.04, 16.04,
  18.04), Linux Mint (17.2, 18.0, 19.0), and macOS installations
    - [apt-get](https://github.com/kenjyco/x200/tree/master/sysinstall/apt-get)
    - [brew](https://github.com/kenjyco/x200/tree/master/sysinstall/brew)
    - **these are mostly no longer used**, in favor of `base` repo
