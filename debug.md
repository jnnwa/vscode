<h1>VSCode Live Debugging</h1>

To use the visual debugger you will need the [C/C++ Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) extension as well as the relevant debug tools for your operating system (Xcode or GDB). If you are on MacOS you will also need the [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb) extension installed. 

<h1>Debug Configuration</h1>

The vscode debug menu can be accessed by clicking the "bug-play-button" in the left menu bar. If you do not have any debug configurations, select `create a launch.json file` to make the config file in `./.vscode/`. Select **LLDB** for MacOS and **GDB** for WSL/CAEN as your environment when prompted (you may need to install GDB on WSL). This will create the default debug configuration file. If you want to make more LLDB/GDB debug configs, you can select the drop down in the debug menu on the top-left and select `Add configuration...`. Usually, you always want this configuration to be `LLDB : Launch` or `GDB : Launch` which will start and run your application from scratch. Once you have a configuration in launch.json, you will should go through these steps to configure it:

1. Change `name` to something meaningful
2. Change `program` to the executable you are interested in debugging (eg. `"program" : "${workspaceFolder}/scheduler"`)
3. Add `args` to be passed into argv (if necessary). It is important to know that the args parameter needs to be specified as an array of strings split on white space. For example, to recreate the command line args `./main arg1 arg2 arg3` you should use `"args" : ["arg1" , "arg2", "arg3"]`
4. (Optinal) `"preLaunchTask"` allows you to specify a task from `tasks.json` to run before you run the launch task. Yo umay find it helpful to set this to your regular build task.

<h2>Input Redirection</h2>

This will be necessary for project 4 only, but you can supply file redirection to the program being debugged.

<h3>MacOS</h3>

Add another field to the respective launch configuration with the format:

`"stdio" : ["input-filepath", "output-filepath", "err-filepath"]`

If you are not using one of the in/out/err redirection fields, leave it as `null`.

<h3>CAEN/WSL</h3>

Add the standard redirection '</>' format to the `"args"` field of your configuration. Example:

`"args" : ["arg1", "arg2", "<input.in", ">output.out"]`

<h2>Apple Silicon</h2>

TODO

<h1>Infrastructure Signal Masking</h1>

The Project infrastructures use system signals that you may need to mask in order to prevent unwanted pauses while stepping. Example:

For GDB, add `"setupCommands" : [{"text":"handle SIGUSR1 nostop noprint"}]`

For LLDB, add `"postRunCommands" : ["process handle SIGUSR1 -n true -p true -s false"]`

<h1>Live Debugging</h1>

Note: The live debugger will only allow you to step through functions and watch variables that are included in the debug symbols of your executable (compile with `-g`). This means you **cannot** see internal infrastructure code or variables.

In the debug menu, select a configuration from the drop down and press play to begin running your program. The debugger will pause when it hits a breakpoint or encounters an error.

The visual interface for debugging is best described in Microsoft's official [guide](https://code.visualstudio.com/docs/editor/debugging) (stepping, breakpoints, watch lists, call stacks, etc.). We will only discuss specific nuances that you should account for in the projects. Here is another Microsoft [guide](https://code.visualstudio.com/docs/cpp/cpp-debug) showing advanced C++ debugging features (threads, core dump, etc.)

<h1>Project 1 and 2</h1>

For this class, the project 1 and 2 implementation of a thread is different from the debugger's expectation. In project 1, you will find that there is only ever one "thread" in the call stack that will appear to switch between the ones you create in the program. For project 2, you will find that the call stack only lists as many threads as you have CPUs defined in boot. These CPU-threads will then switch between the threads you have created within the thread library.

Non-deterministic interrupts are running on a (very fast) timer. This means that if you try to step/pause though your program with them enabled, you will likely find interrupts/context switches everytime you step.

<h1>Project 3 and 4</h1>

When debugging project 3 **applications/tests**, you may find it helpful to also mask the SIGSEV signal in the launch.json.

<h1>The End</h1>

This guide was written as of WN21 and likely suffers from "it works on my machine" syndrome, so if you run into any trouble or find discrepancy with newer versions of software, please post on piazza.
