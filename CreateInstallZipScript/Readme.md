# BakkesMod Plugin Installation Package Creator

This PowerShell script creates an installation ZIP file for BakkesMod plugins. The script automatically detects your project version from `version.h`, packages only the necessary files for end users, and creates a properly structured ZIP that can be easily distributed.

## Features

- 🔍 **Automatic structure detection**: Works with all Visual Studio project configurations
  - Combined solution/project folder
  - Traditional solution with separate project folders
  - Running from a project subfolder
- 📊 **Version extraction**: Automatically reads version information from your `version.h` file
- 📦 **End-user focused**: Packages only the files needed for installation, no source code included
- 🧩 **BakkesMod-ready**: Creates a ZIP with the correct structure for direct extraction to BakkesMod folder

## Requirements

- PowerShell 5.0 or higher
- Windows operating system
- BakkesMod plugin project created with Visual Studio

## Usage

### Basic Usage

1. Place the `create_install_zip.ps1` file in your project or solution folder
2. Open PowerShell in that location
3. Run the script:

```powershell
.\create_install_zip.ps1
```

The script will:

- Detect your project structure and name
- Extract version information from `version.h`
- Generate a properly structured ZIP file in your solution directory
- Display detailed information about what it's copying

### Version File Format

The script expects a `version.h` file in your project directory with content similar to:

```cpp
#define VERSION_MAJOR 1
#define VERSION_MINOR 2
#define VERSION_PATCH 3
#define VERSION_BUILD 456
```

These values will be used to create the output filename: `ProjectName_install_1-2-3-456.zip`

## Output Structure

The generated ZIP file will have the following structure:

```
ProjectName_install_x-x-x-x.zip
├── plugins/
│   ├── ProjectName.dll
│   └── settings/ (if exists)
├── data/ (if exists)
└── cfg/ (if exists)
```

This allows end users to simply extract the ZIP into their BakkesMod directory.

## Troubleshooting

### Common Issues

- **Missing DLL**: If the script reports that your plugin DLL is not found, make sure you've built your project successfully
- **Empty folders**: Empty folders will be detected but skipped during packaging
- **Missing version.h**: If version.h is not found, the script will use default version numbers (1.0.0.0)

### "Script is not digitally signed"

If you get a security error, you may need to adjust your PowerShell execution policy:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

## License

This script is provided as-is with no warranty. Feel free to modify and distribute it as needed for your BakkesMod plugin development.

## Community & Support

Join our Discord community to stay updated on plugin development, share feedback, and get assistance with BakkesMod plugins:

[Join the Discord Server](https://discord.gg/yourserverinvite)

The Discord server is the best place to:

- Get notifications about my new plugin releases
- Report bugs or request features
- Connect with other BakkesMod users
- Receive support for installation and usage issues
- Early access to beta features
