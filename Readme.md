# BakkesMod Development Tools

Welcome to this repository of tools and utilities for BakkesMod plugin development. These resources are designed to streamline the process of creating, packaging, and maintaining BakkesMod plugins for Rocket League.

## Available Tools

### [CreateSourceZipScript](./CreateSourceZipScript)

A PowerShell script that automatically creates a compliant ZIP package for BakkesMod plugin submissions. The script handles different project structures, intelligently selects necessary files, and packages everything according to BakkesMod requirements.

**Key Features:**

- Automatic detection of Visual Studio project structures
- Smart file selection and exclusion
- Preservation of your project organization in the output
- Support for all standard BakkesMod plugin requirements

[Learn more about the CreateSourceZipScript →](./CreateSourceZipScript)

### [CreateInstallScript](./CreateInstallZipScript)

A PowerShell script that generates installation ZIP packages for end users of your BakkesMod plugins. The script extracts version information from your code and packages only the files needed for installation.

**Key Features:**

- Automatic version detection from version.h
- Creates end-user friendly installation packages
- Includes only required files (DLL, settings, etc.)
- Versioned output filenames for easier distribution

[Learn more about the CreateInstallScript →](./CreateInstallZipScript)

## Community & Support

Join our Discord community to stay updated on plugin development, share feedback, and get assistance with BakkesMod plugins:

[Join the Discord Server](https://discord.gg/ycrbhbAKaK)

The Discord server is the best place to:

- Get notifications about new plugin releases
- Report bugs or request features
- Connect with other BakkesMod users
- Receive support for installation and usage issues
- Early access to beta features

## License

All tools in this repository are provided as-is with no warranty. Feel free to modify and distribute them as needed for your BakkesMod plugin development.
