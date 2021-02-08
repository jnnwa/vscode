<h1>VSCode For EECS 482</h1>

VSCode is not your only option to develop code effectively in this class. Learning native linux text editors (like vim) is a very valuable skill that can allow you to pretty much code anytime anywhere, but the learning curve can be intimidating for students used to traditional GUI based IDEs. For projects 2, 3 (especially), and 4, you will find that traditional IDEs are not very useful without an external terminal configured with a specific environment. Vscode wins here by integrating a multiple terminals into the "IDE" and allows very simple customization of the debugging tools.

<h1>Installation</h1>

The supported platforms for development in EECS 482 are on CAEN Linux, Windows Subsystem for Linux (WSL2), and MacOS (x86 or Rosetta).

<h2>CAEN Linux</h2>

If you have physical access to a CAEN Computer, you may skip this step, vscode is already installed by CAEN. Simply type `$ code` in your CAEN terminal to launch vscode.

If you are away from a CAEN Computer but would like to develop using files that are located on your CAEN account, you can remotely establish an SSH connection to CAEN by installing Vscode on your personal computer and using the [Remote-SSH Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh).

<h2>Windows 10</h2>

1. [Download and install Ubuntu with WSL2](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
2. [Download and install vscode for Windows](https://code.visualstudio.com/docs/setup/windows)
3. [Setup WSL development in Windows](https://code.visualstudio.com/docs/remote/wsl)
   
Once installed, always launch vscode as a remote connection to WSL; all your development files should be created and edited within the WSL virtual machine, **not** on your Windows partition.

<h2>MacOS</h2>

1. Ensure Xcode Devtools are up to date
2. Follow the [official installation instructions](https://code.visualstudio.com/docs/setup/mac)

<h3>Apple Silicon Specific Instructions</h3>