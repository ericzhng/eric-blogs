---
title: 'How to set up vs-code for C++ in Windows 10?'
date: 2018-10-10
banner: /eric-blogs/images_posts/vscode_cpp.png
thumbnail: /eric-blogs/images/vs-code.png
categories:
- Software
- vs-code
tags:
  - Windows
  - bash
  - vs-code
  - WSL
---

In this blog, I want to show users how to set up vs-code for C/C++ code in Windows 10 using Linux subsystem, or Windows Subsystem for Linux (WSL).

<!--more-->

## Introduction

I've started following vs-code (Visual Studio Code) since 2017, first in Ubuntu, then in Windows. But I've never actually debugged C/C++ code in Windows using vs-code, mainly because there isn't a C/C++ compiler free of charge provided in Windows, and usually you have to configure a virtual machine [1] in order to debug/run C/C++ program.

Putting that aside, vs-code is such a convenient tool that I definitely recommend for programmers to adopt it. It is much lighter than Visual Studio and also gives users more freedom to configure. 

There are some major steps you need to take, in order to run/debug C/C++ code using vs-code in Windows 10.
 1. Enable Linux Bash shell in Windows 10.
 2. Install vs-code in Windows 10.
 3. Write, debug and run C/C++ code in vs-code.

## 1. Enable Linux Bash shell in Windows 10
 1. Windows 10 Settings -> Update And Security -> For Developers -> Turn on Developer mode.
 2. Control Panel -> Programs -> Windows Subsystem for Linux, check it and click OK to return.
 3. Open Start at lower left of the screen and type in bash, run it.
 4. In the bash.exe, it might prompt a message asking to install the system, type "Y" to continue.
 5. If not, go to Microsoft Store, search for Ubuntu, and install it. You might need to restart the computer.
 6. After installation, create your account and password for Linux.
 7. Every time you want to start bash, either start cmd and type bash, or search for bash directly.
 
## 2. Install vs-code in Windows 10
 1. Downloading newest version vs-code [here](https://code.visualstudio.com/).
 2. Install it in Windows 10.
 3. After installation, you probably want to install a few extensions for C/C++ programming as well. Here is a list of possible extensions you might want to use. Then you are free to go.
   - C/C++
   - C/C++ Intellisense, etc.
 4. The [official website](https://code.visualstudio.com/docs/languages/cpp) contains some pretty good tutorials where you can learn configuring vs-code. 

## 3. Write, debug and run C/C++ code in vs-code.
 1. Create a new folder named test-cpp-vs-code, and use vs-code to open the folder.
   - You can create a test.cpp file in vs-code and copy the following code:
   
	```
	#include <stdio.h>
	#include <math.h>
	#include <iostream>

	int main() {
		char strName[] = "Eric";

		std::cout<< "Hello" << strName << std::endl;

		return 0;
	}
	```
	
 2. Next step, setting up configuration files for vs-code.
   - IntelliSense: generate a `c_cpp_properties.json` file by running **C/Cpp: Edit configurations** command from the Command Palette (Ctrl+Shift+P) and add missing include header directories.
   - Build your code: create a `tasks.json` file by running *Tasks: Configure Tasks* comand in Command Palette, add the compiler information and tasks. To build the prject, run Tasks: Run Build Tasks (Ctrl+Shift+B).
   - Debug your code: generate a launch.json file, by going to Debug view, click the configure icon and then select C++ (Windows) from teh Select Environment dropdown.
   
   - Some common shortcuts: 
     - Format Document: Shift+Alt+F, Ctrl+K/Ctrl+F
     - Search for symbols: Ctrl+Shift+O
	 - Go to definition: F12
	 - To build: Ctrl+Shift+B
 
 For more details about the settings files, please refer to my GitHub repository for the [sample source code](https://github.com/ericzhng/test-vs-code-windows-subsysytem-linux).
 
 **c_cpp_properties.json**
```
{
    "configurations": [
        {
            "name": "WSL",
            "intelliSenseMode": "gcc-x64",
            "compilerPath": "/usr/bin/gcc",
            "includePath": [
                "${workspaceFolder}/**",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/c++/5",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/x86_64-linux-gnu/c++/5",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/c++/5/backward",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/lib/gcc/x86_64-linux-gnu/5/include",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/local/include",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/lib/gcc/x86_64-linux-gnu/5/include-fixed",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/x86_64-linux-gnu",
                "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include"
            ],
            "defines": [
                "__linux__",
                "__x86_64__"
            ],
            "browse": {
                "path": [
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/c++/5",
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/x86_64-linux-gnu/c++/5",
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/lib/gcc/x86_64-linux-gnu/5/include",
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/local/include",
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/lib/gcc/x86_64-linux-gnu/5/include-fixed",
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/x86_64-linux-gnu",
                    "${localappdata}/Packages/CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc/LocalState/rootfs/usr/include/*"
                ],
                "limitSymbolsToIncludedHeaders": true,
                "databaseFilename": ""
            },
            "cStandard": "c11",
            "cppStandard": "c++17"
        }
    ],
    "version": 4
}
```
 
 **tasks.json**
```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "command": "bash",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "command": "g++ -g test.cpp -o maintest.out",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        },
        {
            "label": "run",
            "type": "shell",
            "command": "./maintest.out",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        }
    ]
}
```

 **launch.json**
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Bash on Windows Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "./maintest.out",
            "args": [],
            "stopAtEntry": false,
            // NOTE: you have to specify explicitly the location of files
            "cwd": "/mnt/e/Repos/MyRepos/test-vs-code-windows-subsysytem-linux",
            "environment": [],
            "externalConsole": true,
            "windows": {
                "MIMode": "gdb",
                "setupCommands": [
                    {
                        "description": "Enable pretty-printing for gdb",
                        "text": "-enable-pretty-printing",
                        "ignoreFailures": true
                    }
                ]
            },
            "pipeTransport": {
                "debuggerPath": "/usr/bin/gdb",
                "pipeProgram": "c:\\Windows\\WinSxS\\amd64_microsoft-windows-lxss-bash_31bf3856ad364e35_10.0.17134.1_none_251beae725bc7de5\\bash.exe",
                "pipeArgs": ["-c"],
                "pipeCwd": ""
            },
            "sourceFileMap": {
                "/mnt/c": "c:\\",
                "/mnt/e": "e:\\"
            }
        }
    ]
}
```

Reference:
------
* [1] [Configure complier path using Windows Subsystem for Linux](https://github.com/Microsoft/vscode-cpptools/blob/master/Documentation/LanguageServer/Windows%20Subsystem%20for%20Linux.md).
* [2] [Windows 10's Windows Subsystem for Linux](https://github.com/Microsoft/vscode-cpptools/blob/master/Documentation/Debugger/gdb/Windows%20Subsystem%20for%20Linux.md)
