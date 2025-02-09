---
layout: docs
categories: Installation
permalink: /docs/quickstart/installation/
title: Installation
---


# Nomirun Getting Started Guide

## 1. Install Nomirun

First, you need to download and install the Nomirun command line interface tool (CLI).

### Prerequisites:
1. Download Nomirun installer
2. Microsoft .NET 9.0 SDK (automatically installed)
3. Windows 10/11 (currently only supported OS)
4. Recommended: Powershell Core
<br>
<br>

The installer will:
1. Automatically download Microsoft .NET 9.0 SDK
2. Add Nomirun CLI to PATH variable for Powershell access


<br>
To verify installation, open Powershell and type `nomirun`. You should see:
<br>
```
_ _ _ ____ _ ___
| \ | | ___ _ __ ___ (_) _ __ _ _ _ __ / ___| | | |_ _|
| \| | / _ \ | '_ ` _ \ | | | '__| | | | | | '_ \ | | | | | |
| |\ | | (_) | | | | | | | | | | | | |_| | | | | | _ | |___ | |___ | |
|_| \_| \___/ |_| |_| |_| |_| |_| \__,_| |_| |_| (_) \____| |_____| |___|
```

v1.0.84.0

```
╔═══════NOMIRUN CLI LICENSE════════╗
║                                  ║
║ Customer Name: Trial license     ║
║ License Expires At: 2025-02-28   ║
║ CLI Created At: 2025-01-31       ║
║                                  ║
╚══════════════════════════════════╝
```
<br><br>
### Usage:
```
nomi [OPTIONS] <COMMAND>
```
<br>
### Examples:
```
nomi init
nomi module new --name <MODULE_NAME> --net-version net9.0 --type WebApi --output <CREATE_MODULE_TO>
nomi module run --module-name <MODULE_NAME> --version 1.0.0 --host-framework net9.0
nomi module build --name <MODULE_NAME> --version 1.0.0 --module-csproj "<PATH_TO_CSPROJ>" --nuget-server-name "Local Folder"
nomi module debug --module-csproj "<PATH_TO_CSPROJ>" --module-output "<BUILD_OUTPUT_PATH>" --module-name <MODULE_NAME> --module-id <GUID> --host-framework net9.0
```
<br>
### Options:
- `-h, --help`: Prints help information
- `-v, --version`: Prints version information
<br>
### Commands:
- `init`: Initialize or re-initialize Nomirun CLI. Configure NuGet servers
- `module`: Commands for module related features
- `host`: Commands for host related features
- `create`: Commands for creating different files and outputs
- `generate`: Commands for generating different outputs and enrichments using AI models
<br><br>
## 2. Nomirun Initialize
<br>
Run `nomirun init` to initialize Nomirun on your PC. This will:
- Download the latest version of the Nomirun Host
- Guide you through setting up the Nuget server
<br>
### Supported Nuget Server Options:
1. Azure DevOps
2. GitHub
3. Baget (for local or server installations)
4. Local Folder (recommended for local development)
<br>
You can select one or more options. The wizard will guide you through configuration, which is then stored. Future versions will include more configurations.
<br><br>
## 3. Configure Development Environment
<br>
Supported development environments:
- Visual Studio 2022+
- Jetbrains Rider 2024+
- Visual Studio Code

### Requirements:
- .NET SDK 9.0 (installed automatically with Nomirun CLI)
- For Visual Studio Code: C# Dev Kit required

## 4. Create New Nomirun Module

To create a new module:

```bash
nomirun module new --module-name ToDoService --net-version net9.0 --type WebApi --output d:\Nomirun
```

This generates a new module with initial setup as a .NET library and automatically opens the solution in your IDE.

## 5. Develop and Debug Nomirun Module

### 5.1 Jetbrains Rider 2024+
1. Open module to view Readme.md
2. Build using toolbar icon
3. Run debugger
4. Access server at http://localhost:5310
5. Access Swagger at http://localhost:5310/swagger
   - Default credentials: user/pass

### 5.2 Visual Studio 2022+
1. Build using toolbar icon
2. Run debugger
3. Access server at http://localhost:5310
4. Access Swagger at http://localhost:5310/swagger
   - Default credentials: user/pass

### 5.3 Visual Studio Code
1. Install C# Dev Kit if needed
2. Open module folder
3. Build using toolbar icon
4. Run debugger
5. Access server at http://localhost:5310
6. Access Swagger at http://localhost:5310/swagger
   - Default credentials: user/pass

## 6. Build Nomirun Module

To build as NuGet package:

```bash
nomirun module build --module-name CrmService --version 1.0.0 --module-csproj "d:\Nomirun\CrmService\src\CrmService.csproj" --nuget-server-name "Local Folder"
```

This pushes the module to your configured NuGet server.

## 7. Run Nomirun Module

To run a built module:

```bash
nomirun module run --module-name CrmService --version 1.0.0 --host-framework net9.0
```

This loads the specified NuGet package into the Production Nomirun Host and runs it locally.

**Note**: RELEASE modules must be built before running.
