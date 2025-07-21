# CLI Development Ecosystem & Python Libraries

Building tools that **trust developers** and **amplify productivity** through transparent, composable interfaces.

## What I've Built

A comprehensive ecosystem of 15+ interconnected CLI tools and Python libraries that transform how developers interact with databases, APIs, shell operations, and development workflows. Instead of hiding complexity behind abstractions, these tools illuminate it through **operational transparency** and **human-centric design**.

### Core Philosophy
- **Trust-based architecture** - Assumes developer competence rather than defending against it
- **Operational transparency** - Always shows what's happening under the hood
- **Cognitive ergonomics** - Reduces mental burden through consistent, intuitive interfaces
- **Graceful degradation** - Works reliably across diverse environments

### Key Components

**Shell Environment** ([base](https://github.com/kenjyco/base))
- 900+ shell functions, scripts, and aliases for comprehensive development workflows
- Conditionally defined functions only available when tools they wrap are installed
- Git repository management, Docker orchestration, and environment setup
- Tab completion and vi keybindings for efficient terminal interaction

**Development Environment** ([dotfiles](https://github.com/kenjyco/dotfiles))
- Cross-platform setup script with intelligent backup and symbolic linking
- Vim configuration with Vundle plugin management and vim-tmux-navigator integration
- Tmux configuration with vi keybindings and seamless pane navigation
- Git integration with vimdiff and IPython vi mode for consistent editing experience
- Linux-focused development with macOS compatibility

**Core Libraries**
- [**input-helper**](https://github.com/kenjyco/input-helper) - Data transformations, user interaction patterns, and pre-defined regex
- [**bg-helper**](https://github.com/kenjyco/bg-helper) - CLI orchestration and background task management (git/docker/pyenv)
- [**fs-helper**](https://github.com/kenjyco/fs-helper) - Filesystem operations and production-ready logging
- [**settings-helper**](https://github.com/kenjyco/settings-helper) - Environment-aware configuration management with INI files

These core libraries follow Unix philosophy principles, reinforcing usage of decades-old core utilities (grep, find, xargs, sort, cut, tr) while seamlessly blending with Python. They leverage Python's built-in features extensively and minimize external dependencies, creating a composable foundation that enhances rather than replaces traditional shell workflows.

**Data Management**
- [**dt-helper**](https://github.com/kenjyco/dt-helper) - Human-readable timestamp operations and temporal analysis
- [**redis-helper**](https://github.com/kenjyco/redis-helper) - Redis collections for rapid prototyping and analytics
- [**sql-helper**](https://github.com/kenjyco/sql-helper) - SQLAlchemy wrapper for exploring SQLite, PostgreSQL, and MySQL
- [**mongo-helper**](https://github.com/kenjyco/mongo-helper) - MongoDB wrapper for data analysis and aggregate reporting
- [**webclient-helper**](https://github.com/kenjyco/webclient-helper) - HTTP client with embedded debugging and history tracking

**Specialized Tools**
- [**aws-info-helper**](https://github.com/kenjyco/aws-info-helper) - AWS resource information with three-tier data access
- [**chloop**](https://github.com/kenjyco/chloop) - Character-driven REPL framework backed by Redis
- [**mocp-cli**](https://github.com/kenjyco/mocp-cli) - Interactive music player built on MOC (Music on Console) and chloop
- [**vlc-helper**](https://github.com/kenjyco/vlc-helper) - CLI for precise video control and screenshot capture with VLC media player built on chloop

**Meta-Package** ([libs](https://github.com/kenjyco/libs))
- Flexible installation options: `kenjyco-libs`, `kenjyco-libs[data]`, `kenjyco-libs[full]`, etc.
  - *does not include mocp-cli or vlc-helper*
- `kenjyco-dev-setup` command for local development that clones all repositories and installs them in editable mode
- Enables dogfooding in-progress changes across all repositories within the same environment
- `kenjyco-ipython` command that auto-imports all installed packages, minimizing history clutter from repetitive import statements during testing and experimentation

### How They Work Together

**Consistent Integration Patterns:**
- 2-character imports (`import redis_helper as rh`) create transferable muscle memory
- Universal parameter conventions (`debug=False, timeout=None, exception=False, show=False`)
- Cross-library dependencies that create functional composition
- Docker integration that eliminates infrastructure friction

### Multiplicative Value

Learning one library accelerates learning all others due to consistent patterns. A developer who masters redis-helper's string-based query interface can immediately apply similar patterns across the entire ecosystem.

**Key Advantages:**
- **Compound learning effect** - Knowledge transfers between tools
- **Reduced cognitive load** - Consistent interfaces minimize context switching
- **Operational resilience** - Graceful degradation ensures reliability
- **Human-centric design** - Adapts to developer patterns rather than forcing conformity

### What Makes This Unique

Unlike traditional CLI tools that each require learning unique interfaces, or modern frameworks that hide complexity behind abstractions, this ecosystem:

- **Shows rather than hides** - Complete operational transparency
- **Trusts rather than protects** - Assumes developer competence
- **Composes naturally** - Tools amplify each other's capabilities
- **Evolves gracefully** - New functionality is additive, not disruptive

### Educational Impact

**[Learning Python 3 Notebook](https://gist.github.com/kenjyco/69eeb503125035f21a9d)** - A comprehensive, interactive Python tutorial that has become my most-starred GitHub contribution. This Jupyter notebook provides a systematic progression from basic concepts to advanced topics, emphasizing hands-on learning through executable examples. Available on MyBinder for immediate experimentation, it demonstrates the same philosophy as my CLI ecosystem: making complex concepts accessible through clear, transparent instruction.

### Coming Soon

- **YouTube videos** demonstrating CLI workflows and tool integration
- **Book on shell scripting and Python programming** for beginners, showcasing practical development patterns

### Technologies & Skills

**Languages:** Python, Shell Scripting (Bash/Zsh), SQL
**Databases:** Redis, MongoDB, PostgreSQL, MySQL, SQLite
**Infrastructure:** Docker, AWS, Git
**Specialties:** CLI tool development, Database operations, API integration, Development workflows

### Impact

This ecosystem transforms how developers work with:
- **Database exploration** - Consistent interfaces across Redis, MongoDB, SQL
- **API development** - Transparent HTTP client with debugging capabilities
- **Development workflows** - Comprehensive shell environment with 900+ functions
- **Infrastructure management** - Automatic Docker provisioning and AWS integration
- **Team productivity** - Transferable knowledge and consistent patterns

---

*Building tools that make complex operations naturally composable and immediately transparent.*

