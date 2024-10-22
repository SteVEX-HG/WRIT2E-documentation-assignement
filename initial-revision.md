# How to Install C++ Development Environment On Windows

Want to learn C++ programming but you don't know how to run your own code? Don't worry! This tutorial is going to guide you through the process of setting up a C++ development environment and running your code in the command line. You don't need to have any previous programming experience or pre-installed software on your machine to get started!

> [!Note]
> This tutorial is only intended for ***64-bit*** machines running the ***Windows 10*** operating system, as a C++ development environments varies significantly across different operating systems. 
> - You may use this tutorial for ***Windows 11***. Some of the graphics may be different but the procedure is exactly the same.
>   - ***Never*** use this tutorial for MacOS or Linux systems.
> <br/>
> 
> - Your machine is most likely 64-bit unless it's over a decade old.

## Overview
A C++ Development environment ultimately boils down to a C++ ***compiler***, which makes it possible for Windows to understand your own code, and a ***debugger***, which runs the code in a specific way that helps you fix mistakes in the code. Following this tutorial, you will install the compiler and debugger provided by MinGW-w64. You will also learn the most bare-bone way to write and compile a C++ program, namely with Notepad and the command line. Starting with this most basic form of development environment is a great foundation that will help you understand more advanced environments later on.

---

## Contents
0. [A Very Brief Intro to the Command Line](#0)
1. [Check Compiler Installation](#1)
2. [Install MSYS2](#2)
3. [Update MSYS2](#3)
4. [Install MinGW-w64 Compiler and Debugger](#4)
5. [Add PATH Environment Variable](#5)
6. [Verify Installation](#6)
7. [Create .cpp file](#7)
8. [Compile and Run](#8)
9. [What's Next?](#9)

---

## 0. A Very Brief Intro to the Command Line <a id='0'></a>

Since you will be using the command line terminal quite frequently in the installation process, it's best to get to know it in the beginning. If you are already familiar with the command line, please skip this section.



### What is the command line?
<ul>

The command line is  a text-based interface that allows users to interact directly with a software or the operating system. On Windows, the most frequently used command line is  the ***Command Prompt (cmd)***. Some softwares may come with their own command lines, but the logic behind them is the same.
</ul>

### How to open the Command Prompt?

<ul>

#### i.  Press `Win + R`

- This should open the `Run` window like this:

<ul><img src=".\images\run-window.png" style="width: 300px"></ul>

#### ii. Enter `cmd`, and press `Enter`
- Now you should see the Command Prompt window pop up.

<ul><img src=".\images\command-prompt.png" style="width: 400px"></ul>

</ul>

### How to use the Command Prompt?

<ul>

In the command prompt, you are always on a *current directory* (folder). A ***directory*** is a location on your computer where files are stored. It simply represents the series of folders that you would click through in the file explorer in order to get to that location. The series of folders are separated by backslash `\`. You can see your current directory here:

<img src=".\images\current-directory.png" style="width: 400px"> 

*(In this example, we are in the `Lenovo` folder that's within the `Users` folder that's in the `C` drive)*

Following the current directory, you can type in a command. The command will execute after you press `Enter`, producing output in the command prompt window. It is always in the current directory that your command is executed. For example, the `dir` command lists all the folders and files in the current directory.

<img src=".\images\dir.png" style="width: 400px"> 

After the command output, the current directory is shown again and we can type in another command. For example, the command `cd` changes your current directory. The directory to change into is typed in following `cd`. 

<img src=".\images\cd.png" style="width: 300px"> 

Now our current directory has been changed to `F:\SteamLibrary\steamapps`

</ul>

### More about `cd` and directories

<ul>

There are two types of directories. An ***absolute directory*** gives the full location of the directory. It always starts with a ***root directory***, namely a drive of your computer, such as `C:\` representing the `C` drive. Since an absolute directory contains the full location, you can `cd` to an absolute directory no matter your current directory. The exception is that you can't `cd` to a directory that is located on another root directory (drive). Instead, you must switch the root directory first by directly typing it out. For example:

<img src=".\images\root-directory.png" style="width: 400px">

Here, to get to the absolute directory `F:\SteamLibrary\steamapps` from a current directory in `C:\`, you must first use `F:` command to switch to the `F:\` root directory, then `cd` to the absolute directory.

Another type of directories is the ***relative directory***, which specifies how you would get to it from the current directory. For example, as shown in the diagram, if you are on the current directory `C:\school\math`, then the relative directory `notes\week1` refers to `C:\school\math\notes\week1`.

You can also use `.` and `..` in your directory. `.` simply refers to the current directory, so `.\notes\week1` would be equivalent to `notes\week1`. On the other hand, `..` indicates the ***parent directory***, which is one level up from the current directory. For example, on your current directory `C:\school\math`, the relative directory `..\python\code` would refer to `C:\python\code`.

<img src=".\images\directory.png" style="width: 600px">

</ul>


Now that we have learned about the command line and how to `cd` to a directory, let's begin the installation of the C++ development environment.


## 1. Check Compiler Installation <a id='1'></a>
<ul>

You might already have a C++ compiler installed on your machine. To check this, from any current directory, enter the command `g++ --version` into the command prompt.

- If a copyright message shows up, it means your compiler should be properly installed. Congratulations! You can skip to step 7 to learn how to compiler a c++ file using the command line.
- Otherwise, if you see an error message like this, it means you don't have the g++ compiler installed. You should proceed with this tutorial.
<ul>
<img src=".\images\g++error.png" style="width: 500px"> 
</ul>
</ul>

## 2. Install MSYS2 <a id='2'></a>
<ul>

MSYS2 is a "Software Distribution and Building Platform for Windows". You don't need to know what any of this means. Just know that MSYS2 is a software that helps you install some development tools. To install MSYS2:

#### i. Download MSYS2 installer
- Go to the [MSYS2 Official Website](https://www.msys2.org/). Click the file to download.

<ul><img src=".\images\msys2-download.png" style="width: 500px"> </ul>

#### ii. Run the MSYS2 installer
- Run the installer that you just downloaded.
- Keep clicking on next and go through the installation process. You should have no reason to change the installation settings.
<br>

> [!Warning]
> If for whatever reason you wish to change the installation folder and not use the default folder. Make sure you install MSYS2 into a **new empty folder**. 
</ul>

## 3. Update MSYS2 <a id='3'></a>
<ul>

#### i. Open MSYS2 Command Line
- We need the MSYS2 command line to interact with it. To open the command line, open the start menu (by pressing `Windows`), then search by typing `MSYS2 MSYS`. You should see the `MSYS2 MSYS` app come up. Click on it.

<ul>
<img src=".\images\start-msys2.png" style="width: 300px"> 
</ul>

#### ii. Enter `pacman -Syu` command
- This updates all the local package databases. The command line output should look like this:

> [!Note] 
> ***Copy-Pasting into the command line***
> 
> You can't paste a command in to MSYS2 the command line using `Ctrl + V`. Instead, to paste, right click and select `paste`.

<ul>
<img src=".\images\-syu.png" style="width: 500px"> 
</ul>

#### iii. Enter `Y` to confirm installation
- Wait patiently for the installation to complete. Do not close the command line window during installation. 
- When prompted after installation, enter `Y` to confirm again.

<ul><img src=".\images\y-confirm.png" style="width: 500px"> </ul>

- The command line window will close automatically after confirmation.

</ul>

## 4. Install MinGW-w64 Compiler and Debugger <a id='4'></a>
MinGW-w64 provides Windows versions of the open-source *GNU compiler collection*, which includes the ***gcc*** and ***g++*** compiler and the ***gdb*** debugger. To install MinGW-w64 through MSYS2:
<ul>

#### i. Open the MSYS2 command line, as in STEP 3 - i

#### ii. Enter `pacman -S mingw-w64-x86_64-gcc` command
- This will install gcc and g++ compilers.
<ul>


<img src=".\images\pacman-gcc.png" style="width: 500px"> </ul>

#### iii. Enter `Y` to confirm installation
- Wait for the installation to complete. You should see a cursor that prompts you to enter command after completion.

#### iv. Enter `pacman -S mingw-w64-x86_64-gdb` command
- This will install the gdb debugger.

<ul> <img src=".\images\pacman-gdb.png" style="width: 500px"> </ul>

#### v. Enter `Y` to confirm installation
- You may close the MSYS2 command line window after the installation is complete.

</ul>

## 5. Add PATH Environment Variable <a id='5'></a>

When you enter a command in the command line, the operating system will look for that command in the directories listed in the ***PATH environment variable***, in addition to the current directory. So in order to use the commands for C++ compiler and debugger in any directory, we first need to add their directory to the PATH environment variable. To do this:

<ul>

#### i. Find the directory of your MinGW
- The default directory of MinGW is **`C:\msys64\mingw64\bin`**, unless you have specifically changed the directory when you installed MSYS2.
- You should go to this directory to verify if it exist.

#### ii. Open the environment variable setting
- Open the start menu. Search by typing `environment variable`. 
- Click on the result `Edit the system environment variables`

<ul> <img src=".\images\start-environment.png" style="width: 300px"> </ul>

#### iii. Click on `Environmental Variables...`

<ul> <img src=".\images\variables.png" style="width: 350px"> </ul>

#### iv. Select the `Path` entry in the lower system variables section. Then click `Edit...`

<ul> <img src=".\images\path-edit.png" style="width: 350px"> </ul>

#### v. Click `New`

#### vi. Paste your MinGW directory (`C:\msys64\mingw64\bin` by default) into the new entry. Then click `OK`

<ul> <img src=".\images\enter-variable.png" style="width: 350px"> </ul>

#### vii. Click `OK` 's to close the settings windows

</ul>

## 6. Verify Installation <a id='6'></a>

#### i. Start a new Command Prompt Window

#### ii. Similar to STEP 1, enter the commands `g++ --version`, `gcc --version`, and `gdb --version` into the command prompt, one at a time.

- If all three of them produce copyright messages like the one shown below, great job! You have successfully installed a C++ compiler and debugger. 

<ul><img src=".\images\g++confirm.png" style="width: 500px"></ul>

- Otherwise, if you still get the error message saying that the command cannot be recognized, check the system PATH environment variable again, and make sure to restart the Command Prompt Window.

Now let's try compiling a file through the command line.

## 7. Create .cpp file <a id='7'></a>

The job of the C++ compiler is to turn your code file (called the source file, usually with suffix `.cpp`) into an executable file (with suffix `.exe`) that can be run like any other application on your computer. Let's write a simple C++ program and then test it out.
<ul>

#### i. Create a new folder anywhere on your computer
- You can name the folder anything you like. This is usually called the *project folder* as it contains everything related to a software development project.

#### ii. Show file name extensions
- Select the `view` tab at the top of the file explorer, then check the box `File name extensions`


<ul> <img src=".\images\file-name-extensions.png" style="width: 600px"> </ul> 

- This is necessary so that we could create a file with a `.cpp` suffix.

#### iii. Create a new text file (`.txt`) in the folder.

#### iv. Name the file `main.cpp`
- Make sure the file suffix is changed form `.txt` to `.cpp`. Click `Yes` if warned about changing the file suffix.

<ul> <img src=".\images\change-suffix.png" style="width: 300px"> </ul> 

#### iv. Open the file with a text editor
- To do this, right click on the file. Hover on the `open with` tab, then choose `Notepad` 

<ul> <img src=".\images\open-cpp.png" style="width: 500px"> </ul>

#### v. Paste the following code into the file
<ul>

```
#include<iostream>

int main()
{
    std::cout << "Hello World!" << std::endl;
    return 0;
}
```
</ul>

#### vi. Press `Ctrl + S` to save the file. Then close the Notepad
</ul>

## 8. Compile and Run <a id='8'></a>
<ul>

#### i. Open command prompt

#### ii. `cd` to the directory of your `main.cpp` (the folder you created in STEP 7 - i)
> [!Tip]
> If you find it difficult to navigate through your files with commands, try this instead: 
> 
> **1.** Go into your folder containing the main.cpp file in the file explorer
> 
> **2.** Click on the directory bar near the top of the window so that the directory is selected
> 
> <ul> <img src=".\images\directory-bar.png" style="width: 450px"> </ul>
> 
> **3.** Copy the directory
> 
>  This would be the *absolute directory* of your project folder. You can then directly `cd` to this directory, but make sure to change your root directory first if the project folder is on a different drive.

#### iii. Enter the command `g++ main.cpp -o main.exe`

- In this command, 
  - `g++` invokes the g++ compiler
  - `main.cpp` specifies the source code file
  - `-o` is a *flag* that gives you the option to name the output file
  - `main.exe` specifies the name of the output file
  
- After the command executes, we can see that a `main.exe` has been generated and added to your project folder.

> [!Note]
> Use `g++` to compile `C++` code, and `gcc` to compile `C` code.

#### iv. Enter `main` in the command prompt
- This will run the `main.exe` we just created. You should see `Hello World!` printed in the command prompt.

<ul> <img src=".\images\hello-world.png" style="width: 500px"> </ul>

</ul>

## What's Next? <a id='9'></a>
Congratulations! Now you have a basic C++ development environment working. 

However, you might have noticed that the process of compiling a program is actually quite cumbersome. This is why you would want to get an ***Integrated Development Environment (IDE)***. An IDE is a software that integrates text editor, command line, compiler, debugger, and many other useful tools in a single graphical interface. It also offers many assistive features that will improve your productivity and code readability, such as automated formatting, syntax highlighting, autocomplete, and even AI. The IDE is indeed a very powerful and customizable tool. No wonder why no one really writes code with Notepad these days.

You should start looking into getting an IDE such as [Visual Studio Code](https://code.visualstudio.com/). You will be surprised how the fundamental features of an IDE behind its fancy interface is really just what we have covered in this tutorial.

If you want to learn more about C++ programming, check out this fantastic free [tutorial](https://www.learncpp.com/).

Wish you best of luck in your coding journey!

<br>
<br>

---

#### Reference

LearningLad. *How to Download and Install C Cpp Toolset ( gcc g++ gdb ) in Windows 11 using mingw-w64 and msys2* Youtube, https://www.youtube.com/watch?v=0HD0pqVtsmw