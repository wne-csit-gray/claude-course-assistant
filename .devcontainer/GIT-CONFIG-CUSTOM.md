# DevContainer Git Configuration

This devcontainer is configured to automatically apply git settings when created. Personal git configurations are supported through a custom script that is ignored by git.

## How to Use

### For Personal Git Configuration

1. Create your custom configuration file:

   ```bash
   cp .devcontainer/git-config-custom.sh.example .devcontainer/git-config-custom.sh
   ```

2. Edit `.devcontainer/git-config-custom.sh` with your personal settings:

   ```bash
   # Example content:
   git config --local user.email "your.email@example.com"
   git config --local user.name "Your Name"
   git config --global core.editor "vi"
   ```

3. The custom file is automatically ignored by git, so your personal settings won't be committed to the repository.

4. Rebuild your devcontainer - your custom settings will be applied automatically.

### Files

- `git-config-custom.sh.example` - Example custom configuration file (committed to repo)
- `git-config-custom.sh` - Your personal git configuration (ignored by git)

### Default Configuration

The following git settings are applied by default for all users:

- `core.autocrlf false` - Disable automatic line ending conversion
- `core.eol lf` - Use LF line endings

### Node.js Development Features

This devcontainer includes:

- Node.js 22 (latest LTS)
- npm and yarn package managers
- Essential Node.js development tools
- Docker-in-Docker support
- Common VS Code extensions for Node.js development

### Troubleshooting

If the git configuration isn't working:

1. Check that your custom configuration file exists:

   ```bash
   ls -la .devcontainer/git-config-custom.sh
   ```

2. Manually run your custom script to test it (from workspace directory):

   ```bash
   cd /workspace && bash .devcontainer/git-config-custom.sh
   ```

3. Check the devcontainer creation logs for any error messages.

4. Verify your custom configuration file has proper Unix line endings (LF, not CRLF).

### Example Custom Configuration

Here's an example of what your `git-config-custom.sh` might look like:

```bash
#!/bin/bash
set -e
echo "Applying custom git configuration..."

git config --global user.email "first.last@wne.edu"
git config --global user.name "First Last"
git config --global core.editor "vi"
git config --global init.defaultBranch main

echo "Custom git configuration applied."
```

### Ports

The following ports are automatically forwarded:

- 8080, 8000, 8001 - Original configured ports
- 3000 - Common Node.js/React development port
- 5000 - Common Express.js development port
