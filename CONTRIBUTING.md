# Contributing to Galactica Package Repository

Thank you for your interest in contributing! 🎉

## How to Add a Package

### Step 1: Fork the Repository

Click "Fork" on GitHub to create your own copy.

### Step 2: Create Package File

Create a new `.pkg` file in the appropriate category:

```bash
# Choose the right category
cd editors/    # or shells/, system/, network/, etc.

# Create your package file
nano my-package.pkg
```

### Step 3: Package File Format

```ini
[Package]
name = "my-package"              # Package name (lowercase, use - not _)
version = "1.2.3"                # Version number
description = "Brief description" # One-line description
url = "https://..."              # Source tarball URL
category = "editors"             # Category name

[Dependencies]
depends = "dep1 dep2"            # Space-separated dependencies

[Build]
configure_flags = "--prefix=/usr --enable-feature"
make_flags = "-j$(nproc)"
install_target = "install"       # Usually "install"

[Script]
# Optional: Custom build commands
# Leave empty to use default: ./configure && make && make install
#
# Example for CMake project:
# cmake -B build -DCMAKE_INSTALL_PREFIX=/usr
# cmake --build build -j$(nproc)
# cmake --install build
```

### Step 4: Add to INDEX

Edit the `INDEX` file and add your package:

```bash
# Add in alphabetical order within the category
editors/my-package.pkg
```

### Step 5: Test Locally

```bash
# Test that Dreamland can parse your package
dreamland info my-package

# Try installing it
dreamland install my-package
```

### Step 6: Submit Pull Request

```bash
git add .
git commit -m "Add my-package version 1.2.3"
git push origin main
```

Then open a pull request on GitHub!

## Package Guidelines

### Naming

- Use lowercase
- Use hyphens, not underscores: `my-package` not `my_package`
- Match upstream project name when possible

### URLs

- Link to official source tarballs (not git repos)
- Prefer stable releases over git snapshots
- Use HTTPS when available
- Example: `https://example.org/releases/package-1.2.3.tar.gz`

### Dependencies

- List only direct dependencies
- Use package names as defined in this repository
- Order doesn't matter, use spaces to separate

### Descriptions

- One sentence, clear and concise
- Start with capital letter, no period at end
- Example: "Fast and lightweight text editor"

### Build Instructions

**For Autotools projects** (./configure):
```ini
[Build]
configure_flags = "--prefix=/usr"
make_flags = "-j$(nproc)"
install_target = "install"

[Script]
# Leave empty - will use default
```

**For CMake projects:**
```ini
[Script]
cmake -B build -DCMAKE_INSTALL_PREFIX=/usr
cmake --build build -j$(nproc)
cmake --install build
```

**For Make-only projects:**
```ini
[Script]
make -j$(nproc) PREFIX=/usr
make install PREFIX=/usr
```

**For Python projects:**
```ini
[Script]
python setup.py build
python setup.py install --prefix=/usr
```

## Categories

Choose the most appropriate category:

- **editors** - Text editors, IDEs
- **shells** - Command-line shells
- **system** - Core system utilities
- **network** - Network tools and clients
- **development** - Compilers, interpreters, build tools
- **desktop** - Window managers, desktop environments
- **multimedia** - Audio, video, image tools
- **games** - Games and entertainment
- **security** - Security and privacy tools
- **web** - Web servers, browsers
- **databases** - Database systems
- **libraries** - Shared libraries

If unsure, ask in your pull request!

## Pull Request Process

1. **Title:** "Add package-name version X.Y.Z"
2. **Description:** Briefly explain what the package does
3. **Testing:** Confirm you tested the installation
4. **One package per PR:** Makes review easier

### Example PR Description

```
Adds helix version 23.10

Helix is a modern modal text editor with tree-sitter support.

Tested on Galactica Linux:
- [x] Package parses correctly
- [x] Builds successfully
- [x] Installs to /usr
- [x] Binary runs without errors

Dependencies: tree-sitter, rust
```

## Code of Conduct

- Be respectful and welcoming
- Focus on constructive feedback
- Help newcomers learn
- Have fun building together!

## Need Help?

- Open an issue with the "question" label
- Ask in GitHub Discussions
- Check existing packages for examples

## Advanced Topics

### Patches

If upstream source needs patches:

```ini
[Script]
# Apply patch before building
patch -p1 < fix-compilation.patch

./configure --prefix=/usr
make -j$(nproc)
make install
```

Include the patch file in the repository.

### Multiple Variants

For packages with different build options, create variants:

```
editors/vim.pkg           # Basic vim
editors/vim-full.pkg      # Vim with all features
editors/vim-minimal.pkg   # Tiny vim
```

### Version Updates

When updating versions:

1. Test the new version thoroughly
2. Update `version` field
3. Update `url` to new tarball
4. Update dependencies if changed
5. PR title: "Update package-name to X.Y.Z"

## Recognition

Contributors are listed in the repository and their packages show their GitHub username:

```bash
dreamland info package
# Maintained by: @YourGitHubUsername
```

Thank you for making Galactica better! ✨
