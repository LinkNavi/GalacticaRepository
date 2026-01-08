# 🌌 Galactica Package Repository

Official package repository for [Galactica Linux](https://github.com/YourUsername/Galactica).

## 📦 What is this?

This repository contains package definitions (`.pkg` files) for software that can be installed on Galactica Linux using the **Dreamland** package manager.

Dreamland is a source-based package manager that builds software from source, similar to Gentoo's Portage or FreeBSD's Ports, but with a modern, user-friendly interface.

## 🎨 Package Categories

- **editors/** - Text editors (vim, emacs, nano, etc.)
- **shells/** - Command-line shells (bash, zsh, fish)
- **system/** - Core system utilities
- **network/** - Network tools and utilities
- **development/** - Programming languages and dev tools
- **desktop/** - Window managers and desktop environments
- **multimedia/** - Audio/video tools
- **games/** - Games and entertainment
- **security/** - Security and privacy tools
- **web/** - Web servers and tools
- **databases/** - Database systems
- **libraries/** - Shared libraries and dependencies

## 🚀 Usage

### For Users

```bash
# Sync package repository
dreamland sync

# Search for packages
dreamland search vim

# Install a package
dreamland install vim

# List installed packages
dreamland list
```

### For Package Maintainers

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to add packages.

## 📝 Package Format

Packages are defined in `.pkg` files with this format:

```ini
[Package]
name = "package-name"
version = "1.2.3"
description = "What this package does"
url = "https://source-tarball-url.tar.gz"
category = "category-name"

[Dependencies]
depends = "dependency1 dependency2"

[Build]
configure_flags = "--prefix=/usr"
make_flags = "-j$(nproc)"
install_target = "install"

[Script]
# Optional custom build commands
# If not provided, uses: ./configure && make && make install
```

## 🔒 Security

All packages:
- Are built from source (no pre-compiled binaries)
- Link to official upstream sources
- Can be audited by viewing the `.pkg` file
- Use checksums for verification (coming soon)

## 🤝 Contributing

We welcome contributions! To add a package:

1. Fork this repository
2. Create a new `.pkg` file in the appropriate category
3. Add the package to `INDEX`
4. Test with `dreamland install your-package`
5. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

## 📊 Statistics

- **Total packages:** 50+
- **Categories:** 12
- **Contributors:** Community-driven
- **Update frequency:** Rolling release

## 🌟 Featured Packages

### Editors
- **vim** - The ubiquitous text editor
- **neovim** - Hyperextensible Vim-based editor
- **helix** - Modern modal editor

### Development
- **python** - Popular programming language
- **rust** - Systems programming language
- **nodejs** - JavaScript runtime

### System
- **coreutils** - GNU core utilities
- **openssh** - Secure shell access

## 📖 Documentation

- [Package Format Specification](docs/PACKAGE_FORMAT.md)
- [Build System Guide](docs/BUILD_SYSTEM.md)
- [Contributing Guide](CONTRIBUTING.md)

## 💬 Community

- **Issues:** Report bugs or request packages via GitHub Issues
- **Discussions:** General discussion on GitHub Discussions
- **Matrix:** #galactica:matrix.org (coming soon)

## 📜 License

- Package definitions: MIT License
- Individual software packages: Licensed under their respective licenses

## 🎀 Philosophy

Galactica believes in:
- **Transparency** - All build scripts visible
- **Choice** - You control your system
- **Simplicity** - Easy to understand and modify
- **Community** - Built by users, for users

---

**Built with love for the Galactica Linux community** ✨
