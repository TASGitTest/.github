# Environment Setup

# Install Tools
I will be going over the install and set-up of these tools:
- Git
- GitHub CLI
- VS Code
- L5Xplode and L5Xgit

Note: While you are under no obligation to use VS Code as your IDE, and I may not later if I can find something that is easier to develop for, this is what I am currently working with.

## VS Code
Download: https://code.visualstudio.com/download
The simplest way to install is to hit the windows key and type "vs code" and then enter. The Microsoft store will pop up and you can click install on the VS Code app. Once installed click the icon on the left ribbon for extensions (looks like 4 squares with one turned 90°). You will want the Git, GitHub, and Structured Text extensions. 

## Git
Download: https://git-scm.com/downloads/win
Click on the above link and select Git for Windows/x64 Setup. Once downloaded you can run the executable and it will install. It will ask you a lot of questions during the install. Go with the recommended, which is not always the one that is highlighted by default. For instance, do not select Vim as the default editor for Git. That way lies madness.

## GitHub CLI
Download: https://cli.github.com/
This will allow for pushes to the repo from the command line. I use this when I make a new repo. Be sure to authenticate:
- `gh auth login`
- This command will allow you to authenticate from your shell so you can push to your repos

## L5Xplode and L5Xgit
Download: https://github.com/RockwellAutomation/ra-logix-designer-vcs-custom-tools
Repo: RockwellAutomation/ra-logix-designer-vcs-custom-tools

### Dependencies
There are a few requirements to using this tool: 
- Studio 5000
- Logix Designer SDK available on the Rockwell Product Compatibility site
- .Net 8.0 SDK 
	- Download: https://dotnet.microsoft.com/en-us/download

If you don't have the Logix Designer SDK, it is available on the Rockwell Product Compatibility & Downloads Center. 

### Build
Once the SDKs are installed you can install this tool in the command line:

``` bash
# Navigate to the folder you want to copy the repo to:
cd C:\{YOUR FOLDER PATH HERE}
# Use github cli to clone the repo:
gh repo clone RockwellAutomation/ra-logix-designer-vcs-custom-tools
# Navigate to the repo:
cd ra-logix-designer-vcs-custom-tools
# Build the project:
dotnet build -c Release
```

This creates the programs you need to 'explode' and 'implode' L5X files and, in theory, convert .ACD binaries to .L5X. I haven't been able to get this to work yet. While the programs are usable in this state, I would recommend adding them to your PATH variable so they can be accessible in your whole system. To do that:

- Press the windows key and type 'environment variables' and click the option that says 'Edit the system environment variables'
- Click the 'Environment Variables...' button
- Select the Path variable and click the 'Edit...' button
- Click 'New' and type in the directory for the repo plus the following:
	- `{REPO FILE PATH}\bin\Release`

### Studio 5000 Integration
To add git functionality to Logix Designer:
- Open the file explorer and navigate to the repo Assets folder:
	- `~\artifacts\bin\release\Assets\`
- Inside you should find the `CustomToolsMenu.xml` file. Copy it and place it in this folder:
	- `C:\Program Files (x86)\Rockwell Software\RSLogix 5000\Common\`

