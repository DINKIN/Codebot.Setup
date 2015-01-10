# Free Pascal and Lazarus Trunk Setup

This guide will assist users in compiling and configuring the latest
versions of the Free Pascal Compiler and Lazarus IDE. The source code
for these projects will be pulled from their official subversion
repositories.

This guide is for all operating systems.

## Setting up your paths

Create a folder to store the compiler, IDE, and other tools. In this 
guide I use the variable BASE ro refer to the $HOME/Development/Base
folder, but you can use whatever folder name or location you prefer.

Open a terminal and create your base folder.

Debian/Ubuntu:
```
BASE=$HOME/Development/Base
mkdir $BASE
```
Windows:
```
set BASE=C:\Development\Base
mkdir %BASE%
```

### Install the prerequisites

Before you begin you need to install the build system and subversion 
tools. If you don't already have them setup, follow these steps.

Debian/Ubuntu:
```
sudo apt-get install build-essentials subversion
```
Windows:

1. Download [bintools.zip](http://cache.codebot.org/bintools.zip)
2. Extract the files to C:\Development\Base\bintools
3. Add C:\Development\Base\bintools to your path

Type 'svn help' into the terminal. You should see a help listing for the
subversion program.

## Setting up a trunk version of Free Pascal

Download and a working binary version of the Free Pascal 
Compiler 2.6.4 for your platform:

- [FPC 2.6.4 for Debian/Ubuntu 32-bit](http://sourceforge.net/projects/freepascal/files/Linux/2.6.4/fpc-2.6.4.i386-linux.tar/download)
- [FPC 2.6.4 for Debian/Ubuntu 64-bit](http://sourceforge.net/projects/freepascal/files/Linux/2.6.4/fpc-2.6.4.x86_64-linux.tar/download)
- [FPC 2.6.4 for Windows](http://sourceforge.net/projects/freepascal/files/Win32/2.6.4/)

Extract the files from the downloaded archive. Open a terminal in the 
directory containing the contents of the and run the setup script. When
the script asks for the install folder, it to $BASE/fpc-2.6.4 on Linux
or %BASE%\fpc-2.6.4 on Windows.

In your terminal add the following folder to your path, but first save 
the old path.

Debian/Ubuntu:
```
OLD_PATH=$PATH
PATH=$PATH:$BASE/fpc-2.6.4/bin
```

Windows:
```
set OLD_PATH=$PATH
set PATH=%PATH%;%BASE%\fpc-2.6.4\bin\i386-win32
```

Type 'fpc' into the terminal. You should see a help listing for the
Free Pascal Compiler listing version 2.6.4.

Get the trunk version of fpc from svn (a revision number is optional).
`svn co [-r rev#] http://svn.freepascal.org/svn/fpc/trunk fpc

Build the fpc trunk compiler.
```
cd fpc
make all
make install PREFIX=<current path>
```
Close the terminal then open a new one.

Add the newly created fpc bin folder to your PATH variable.

To get a

`svn co [-r rev#] http://svn.freepascal.org/svn/lazarus/trunk lazarus

To compile

`make all

## Setting up Free Pascal for cross compiling to other platforms

Some cross installation examples

```
cd fpc
make crossinstall PREFIX=<current path> OS_TARGET=linux CPU_TARGET=i386
make crossinstall PREFIX=<current path> OS_TARGET=linux CPU_TARGET=x86_64
make crossinstall PREFIX=<current path> OS_TARGET=win32 CPU_TARGET=i386
make crossinstall PREFIX=<current path> OS_TARGET=win64 CPU_TARGET=x86_64
make crossinstall PREFIX=<current path> OS_TARGET=android CPU_TARGET=arm 
```
