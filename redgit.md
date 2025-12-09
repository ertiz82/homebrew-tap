# Homebrew Formula for RedGit

This directory contains the Homebrew formula for installing RedGit via Homebrew.

## Installation

```bash
# Add the tap
brew tap ertiz82/tap

# Install RedGit
brew install redgit
```

Or in a single command:

```bash
brew install ertiz82/tap/redgit
```

## Usage After Installation

```bash
# Verify installation
rg --version

# Initialize in your project
cd your-project
rg init

# Analyze and commit changes
rg propose

# Push and complete issues
rg push
```

## Updating

```bash
brew update
brew upgrade redgit
```

## Uninstalling

```bash
brew uninstall redgit
brew untap ertiz82/tap  # Optional: remove the tap
```

## Formula Maintenance

### Updating the Formula for New Releases

When a new version is released on PyPI:

1. **Get the new SHA256 hash:**
   ```bash
   curl -sL "https://files.pythonhosted.org/packages/source/r/redgit/redgit-X.X.X.tar.gz" | shasum -a 256
   ```

2. **Update `redgit.rb`:**
   - Change `url` to the new version
   - Update `sha256` with the new hash

3. **Push to homebrew-tap repository:**
   ```bash
   cd /path/to/homebrew-tap
   cp /path/to/redgit/Formula/redgit.rb .
   git add redgit.rb
   git commit -m "Update redgit to vX.X.X"
   git push
   ```

### Updating Dependency Hashes

If dependency checksums fail, get the correct hashes:

```bash
# Typer
curl -sL "https://files.pythonhosted.org/packages/source/t/typer/typer-0.12.5.tar.gz" | shasum -a 256

# Rich
curl -sL "https://files.pythonhosted.org/packages/source/r/rich/rich-13.9.4.tar.gz" | shasum -a 256

# PyYAML
curl -sL "https://files.pythonhosted.org/packages/source/p/pyyaml/pyyaml-6.0.2.tar.gz" | shasum -a 256

# GitPython
curl -sL "https://files.pythonhosted.org/packages/source/g/gitpython/GitPython-3.1.43.tar.gz" | shasum -a 256

# Requests
curl -sL "https://files.pythonhosted.org/packages/source/r/requests/requests-2.32.3.tar.gz" | shasum -a 256
```

### Testing the Formula Locally

```bash
# Audit the formula
brew audit --strict Formula/redgit.rb

# Test installation from local formula
brew install --build-from-source Formula/redgit.rb

# Run tests
brew test redgit
```

## Troubleshooting

### Checksum Mismatch Errors

If you see checksum errors during installation:

```bash
# Clear Homebrew cache
brew cleanup -s
rm -rf $(brew --cache)/downloads/*redgit*

# Reinstall
brew untap ertiz82/tap
brew tap ertiz82/tap
brew install redgit
```

### Formula Not Found

Make sure the tap is added:

```bash
brew tap ertiz82/tap
brew tap  # List all taps to verify
```

### Python Version Issues

The formula requires Python 3.11. If you have issues:

```bash
brew install python@3.11
brew link python@3.11
```

## Related Links

- **Main Repository:** [github.com/ertiz82/redgit](https://github.com/ertiz82/redgit)
- **Homebrew Tap:** [github.com/ertiz82/homebrew-tap](https://github.com/ertiz82/homebrew-tap)
- **PyPI Package:** [pypi.org/project/redgit](https://pypi.org/project/redgit/)
- **Documentation:** [github.com/ertiz82/redgit/tree/main/docs](https://github.com/ertiz82/redgit/tree/main/docs)

## Alternative Installation Methods

If Homebrew doesn't work for you:

```bash
# Using pip
pip install redgit

# From source
git clone https://github.com/ertiz82/redgit.git
cd redgit
pip install -e .
```

## License

MIT License - see [LICENSE](../LICENSE) for details.