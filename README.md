I help developers get the most out of open-source and the data they have access
to through safe experimentation so they can craft maintainable software that
delights customers while reducing future development headaches. I am also
empathetic to less-technical individuals and students learning how they can
build their own tools to explore their curiosities in an organized way.

I create custom developer tooling for innovative ways to interact with data,
build maintainable libraries, develop insightful reports, maximize software
delivery, and minimize technical debt. I’ve been shell scripting (Bash/Linux)
since 2004, using Python since 2007, and maintaining packages on the Python
Package Index since 2017.

Check out:

- [Learning Python 3 gist](https://gist.github.com/kenjyco/69eeb503125035f21a9d)
  if you are new to Python
- [base repo](https://github.com/kenjyco/base) with helpful shell wrappers to
  core utility programs to maximize your command-line developement experience
- [dotfiles repo](https://github.com/kenjyco/dotfiles) with my Linux and Mac
  config files for vim (editing text files), tmux (splitting your terminal
  window), git (managing source code for projects), and more
- [bg-helper repo](https://github.com/kenjyco/bg-helper) one of my core Python
  packages to bridge the gap between Python and Bash for automation, package
  management, testing with docker, managing git repos, and SSH

# Files and Directories

All files, no matter their type (text, image, audio, video, binary, etc) are
just collections of bytes representing data, saved to a storage medium like a
hard drive or USB flash drive. The contents of those bytes differ based on the
purpose and format of the file. Text files are sequences of characters encoded
in specific formats like ASCII or UTF-8. Image files are represented as pixels
with color information encoded in formats like JPEG, PNG, or BMP. Video and
audio files use codecs to organize frames and sound frequencies stored in
formats like MP4, AVI, or MP3. Binary files like executables contain
machine-readable instructions.

Various programs interpret the bytes in files according to the file's format. A
text editor interprets byte sequences as text to display for reading or editing.
An image viewer translates bytes into pixels and color to view. A video player
decodes and renders multimedia files frame by frame. A web server serves files
like HTML, CSS and JavaScript to browsers over the internet. A database stores,
retrieves, and manipulates data stored in structured formats.

Directories (or folders) provide a way to structure files in a hierarchical
manner, so users can organize and group their data in ways that make sense to
them on their *filesystem*. Directories are special files that contain references
to other files or directories. Filesystems have a single *root directory* that
serves as the starting point of the hierarchy. Every file and directory on the
system is contained in the root directory.

The files and directories on the filesystem all have metadata (data about data)
that can tell you things like the file size in bytes, the owner of the file,
what permissions it has (read, write, or execute), when the file was last
modified, and more. Many files have file extensions at the end of their file
names like `.txt`, `.pdf`, `.mp3`. These extensions can be changed, but changing
a file's extension doesn't change its internal signature or metadata.

Try to use clear and consistent naming conventions for files and directories to
keep your system organized, easy to navigate, and quick to understand.

# Command-line Interfaces

The command-line interface (CLI) allows you to use your keyboard to interact
with your computer's operating system (Windows, macOS, GNU/Linux, etc) and the
files of data it contains in an efficient way, without needing to navigate
through a graphical interface. This can be especially effective when you know
the exact operation(s) you want to perform.

You can run programs to do things with your files, get real-time information
about the system you are running, start long-running background processes,
configure interactive servers, connect to other systems on your network, access
resources/data online through APIs, filter through information based on
patterns, reshape data for your needs, explore projects of source code in
various programming languages, interact with databases, and much more.

To use the command-line, you typically open up a terminal program that starts
your login shell (Bash or Zsh) which provides a prompt where you can type
commands. The shell manages your environment, parses commands you type, and
executes them as separate processes. When you first start a new shell, you
usually start in the *home directory* for your user, which makes it convenient
to operate on files you own. Before you are presented with the prompt to enter
commands, your *shell initialization file* is loaded (the `~/.bashrc` file for
Bash or `~/.zshrc` file for Zsh), which allows you to take advantage of
environment customizations you have configured. Those *init files* allow you to
set *environment variables*, define shell functions/aliases, change the info
displayed in your prompt, load *completions*, and more.

When the name of a command is parsed by the shell, it looks through the various
locations in your `PATH` environment variable to see where the command exists
so it can be invoked. Most commands can have their behavior modified using
*short options* (a dash followed by a letter) or *long options* (a double dash
followed by a word). You can usually specify *arguments* to the command (like a
filename, a directory name, a shell pattern matching several file/directory
names, a simple string of characters, a URL to a website, etc). Some options to
a command may accept their own arguments. When using multiple short options, you
can combine multiple letters for various short options to the single dash (as
long as the option isn't one that is expecting its own argument).
