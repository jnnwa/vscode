<h1>VSCode Live Debugging</h1>

To use the visual debugger you will need the [C/C++ Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) extension. If you are on MacOS you will also need the [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb) extension installed. 

<h1>Debug Configuration</h1>

The vscode debug menu can be accessed by clicking the "bug-play-button" in the left menu bar. If you do not have any debug configurations, select a launch.json file to make the config file in `./.vscode/`. Select **LLDB** for MacOS and **GDB** for WSL/CAEN as your environment when prompted (you may need to install GDB on WSL). This will create the default debug configuration file. If you want to make more LLDB/GDB debug configs, you can select the drop down in the debug menu on the top-left and select `Add configuration...`. Usually, you always want this configuration to be `LLDB : Launch` or `GDB : Launch` which will start and run your application from scratch. Once you have a configuration in launch.json, you will should go through these steps to configure it:

1. Change `name` to something meaningful
2. Change `program` to the executable you are interested in debugging (eg. `"program" : "${workspaceFolder}/scheduler"`)
3. Add `args` to be passed into argv (if necessary). It is important to know that the args parameter needs to be specified as an array of strings split on white space. For example, to recreate the command line args `./main arg1 arg2 arg3` you should use `"args" : ["arg1" , "arg2", "arg3"]`
4. (Optinal) `"preLaunchTask"` allows you to specify a task from `tasks.json` to run before you run the launch task. Yo umay find it helpful to set this to your regular build task.

<h2>Input Redirection</h2>
<h3>MacOS</h3>
<h3>CAEN/WSL</h3>

<h2>Apple Silicon</h2>

TODO

<h1>Infrastructure Signal Masking</h1>

The Projects' infrastructures use OS signals that you may need to mask in order to prevent spurious pauses while live debugging.

For GDB, add `"setupCommands" : []`

For LLDB, add `"postRunCOmmands" : []`

handle SIGUSR1 nostop noprint
handle SIGSEGV nostop noprint

<h1>Live Debugging</h1>

Note: The live debugger will only allow you to step through functions and watch variables that are included in the debug symbols of your executable (compile with `-g`). This means you **cannot** see internal infrastructure code or variables.

In the debug menu, select a configuration from the drop down and press play to begin running your program. The debugger will pause when it hits a breakpoint or encounters an error.

<h2>Control Panel</h2>
<h2>Breakpoints</h2>
<h2>Variables</h2>
<h2>Watch List</h2>
<h2>Call Stack</h2>


<h1>Project 1 and 2</h1>


<h1>Project 3 and 4</h1>
