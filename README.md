<h1>VSCode For EECS 482</h1>

VSCode is not your only option to develop code effectively in this class. Learning native linux text editors (like vim) is a very valuable skill that can allow you to pretty much code anytime anywhere, but the learning curve can be intimidating for students used to traditional GUI based IDEs. For projects 2, 3 (especially), and 4, you will find that traditional IDEs are not very useful without an external terminal configured with a specific configuration. Vscode wins here by integrating a multiple terminals into the "IDE" and allows very simple customization of the debugging tools.

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

<h2>Apple Silicon Specific Instructions</h2>

TODO

<h1>Getting Started</h1>

Before we discuss development, there are some critical features and extensions to know about in vscode.

<h2>User Interface</h2>
   
* Bring up your integrated terminal by pressing <kbd>CTRL</kbd>+<kbd>`</kbd> (that is the backtick located above your <kbd>TAB</kbd> key). This terminal defaults opening in the current working directory. The terminal will default to whatever your OS is (Bash for CAEN and WSL, and Zsh for MacOS)
* On the left hand side are the menu options. From the top down (by default): File Browser (cwd), Search, Git, Debugging, and Extensions)

<h2>Necessary Extensions</h2>
You will find the following extensions very useful.

- [C/C++ Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb) (only necessary for MacOS debugging)
- [Remote-SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) (for editing files remotely using SSH)
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) (allows Google Docs style collaboration)

If you are using WSL or any other Remote SSH session, you may find that you have to install an extenstion "twice" because vscode is actually installed both on your local machine and the remote machine (WSL/CAEN). 

There are many other extensions that let you customize autoformatting, icons, etc. feel free to check them out.

<h1>Building</h1>

The integrated terminal in vscode is automatically launched within your working directory, so you can do all make and git commands there. If you want a more 'visual' experience, vscode has an integrated build system that allows you to creat build tasks.

<h2>Adding a Build Task</h2>

From the menu bar, select <kbd>Terminal</kbd>><kbd>Configure Tasks</kbd>. If you have no tasks yet, select create "tasks.json" from template. This will create a json file describing all your tasks in `./.vscode/tasks.json` as an array of json objects. This basic type of task is a `shell` task. The `label` is the name of the task, and the command is whatever command line you want. In this repo is an example `./.vscode/tasks.json` that would build and clean the scheduler for project 1. 


<h1>Running and Debugging</h1>

The integrated terminal in vscode is automatically launched within your working directory, so you can run executables and scripts manually as well as use gdb/lldb if you like. If you want to use the Visual Debugger for vscode see the [debug.md](./debug.md) file in this repository. Note that vscode allows for you to have multiple terminals open at once. <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>`</kbd> to open a new terminal. <kbd>CMD</kbd>+<kbd>\\</kbd> or <kbd>WIN</kbd>+<kbd>\\</kbd> to open terminals side by side to each other (this will be useful for projects 3 and 4).
<h1>Miscellaneous</h1>

<h2>CAEN Remote-SSH 1-Time Auth Settings</h2>