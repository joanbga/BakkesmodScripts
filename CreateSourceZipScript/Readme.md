# BakkesMod Source Package Creator

This PowerShell script creates a ZIP file compliant with BakkesMod plugin review requirements. It automatically detects the project structure, copies the necessary files, and packages them correctly.

## Features

- 🔍 **Automatic structure detection**: Works with all Visual Studio project configurations
  - Combined solution/project folder (when "Place solution and project in the same folder" option is used)
  - Traditional solution with separate project folders
  - Running from a project subfolder
- 📁 **Smart file selection**: Copies only relevant files, excluding debug files
- 🔄 **Configurable folder selection**: Easily add or remove specific folders to include
- 📦 **BakkesMod-compliant packaging**: Creates a ZIP with the correct structure for plugin submission

## Requirements

- PowerShell 5.0 or higher
- Windows operating system
- BakkesMod plugin project created with Visual Studio and BakkesPluginTemplate

## Usage

### Basic Usage

1. Place the `create_source_zip.ps1` file in your project or solution folder
2. Open PowerShell in that location
3. Run the script:

```powershell
.\create_source_zip.ps1
```

The script will:

- Detect your project structure
- Generate a properly structured ZIP file in your solution directory
- Display detailed information about what it's copying

### Customizing the Script

#### Adding/Removing Specific Folders

Edit the `$sourceFolders` array to include any special folders that should be copied:

```powershell
$sourceFolders = @("IMGUI", "YourCustomFolder", "fmt", "AND SO ON...")
```

This is useful for ensuring specific folders are properly copied while avoiding unnecessary ones like `.git`.

#### Additional Output Folders

The script automatically creates these folders in the output ZIP:

- `source/` - Contains all source code
- `plugins/` - Contains the compiled plugin DLL
- Additional folders (if they exist):
  - `data/`
  - `cfg/`
  - `plugins/settings/`

## Output Structure

The generated ZIP file will have a structure that preserves your original project organization:

### For traditional solutions with separate project folders:

```
ProjectName_source.zip
├── source/
│   ├── *.sln
│   ├── ProjectName/
│   │   ├── *.cpp, *.h
│   │   ├── IMGUI/
│   │   └── ...
│   └── ...
├── plugins/
│   ├── ProjectName.dll
│   └── settings/ (if exists)
├── data/ (if exists)
└── cfg/ (if exists)
```

### For combined solution/project structure (when "Place solution and project in the same folder" is checked):

```
ProjectName_source.zip
├── source/
│   ├── *.sln        # Solution files at the root level
│   ├── *.vcxproj    # Project files at the root level
│   ├── *.cpp, *.h   # Source files at the root level
│   ├── IMGUI/
│   └── ...
├── plugins/
│   ├── ProjectName.dll
│   └── settings/ (if exists)
├── data/ (if exists)
└── cfg/ (if exists)
```

The script automatically detects your project structure and preserves it in the output ZIP.

## Troubleshooting

### "Script is not digitally signed"

If you get a security error, you may need to adjust your PowerShell execution policy:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### Common Issues

- **Missing DLL**: If the script reports that your plugin DLL is not found, make sure you've built your project successfully
- **Empty folders**: Empty folders will be detected but skipped during packaging
- **Project detection failure**: If the script cannot detect your project properly, verify that your .vcxproj files are in the expected locations

## License

This script is provided as-is with no warranty. Feel free to modify and distribute it as needed for your BakkesMod plugin development.

## Community & Support

Join our Discord community to stay updated on my plugins development, share feedback, and get assistance with my BakkesMod plugins:

[Join the Discord Server](https://discord.gg/ycrbhbAKaK)

The Discord server is the best place to:

- Get notifications about my new plugin releases
- Report bugs or request features
- Connect with other BakkesMod users
- Receive support for installation and usage issues
- Early access to beta features
