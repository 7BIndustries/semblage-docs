# Developer Setup

## Introduction

Semblage is built using the [Godot game engine](https://godotengine.org/) (using GDScript), and a plugin for Godot called [Godot Python](https://github.com/touilleMan/godot-python). Both of these need to be installed, along with a set of dependencies, for Semblage to work properly. This guide will walk developers through that process, and will also explain the export process to get a Semblage package ready for distribution. These steps should be similar (but not exactly the same) on Windows, Mac OS and Linux.

## Godot Installation

Godot is a single file distributable, which can be downloaded [here](https://godotengine.org/download). The version that is currently used for Semblage is 3.2.x. Download the package for your operating system, and extract it. There should be a binary within the archive. Put this in a location where it is easy to run during the development process.

## godot-python Installation

There are installation instructions in the [godot-python readme](https://github.com/touilleMan/godot-python/blob/master/README.rst), but the steps below should result in a working Godot Python installation.

1. Start Godot
2. Click on the AssetLib tab
3. Click in the search box and enter `python`
4. Click the `Search` button
5. Click on the `PythonScript` item
6. In the dialog that comes up, click the `Download` button
7. Once the download is complete, click the `Install...` button
8. Click the `Install` button in the `Package Installer` dialog

It will take some time, but once the installation is complete, click the `OK` button and you should be able to move to the next step.

## Install pip in Godot Python Environment

These paths here are based on the Linux operating system. Change the path style to match your operating system, and replace `x11-64` with the directory for your operating system. You may need to set the execute bit for the `python3.8` binary in Linux and MacOS.

1. Install pip in the godot-python environment: `./addons/pythonscript/x11-64/bin/python3.8 -m ensurepip`

## pip Requirements Installation

Change the path style to match your operating system, and replace `x11-64` with the directory for your operating system.

1. Install Semblage Python requirements: `./addons/pythonscript/x11-64/bin/python3.8 -m pip install -r requirements.txt`

## CadQuery Library Installation

If you do not care about updating CadQuery, it can be cloned or downloaded from [GitHub](), and then the `cadquery` directory can be copied to the `./addons/pythonscript/x11-64/lib/python3.8/site-packages` directory. You can choose whether or not to install the latest master, or a stable version.

## Manual OCP DLL Installation

The OCP library and its dependencies must be downloaded and copied to the correct directory manually. Use the following steps, modifying the paths and `x11-64` directory name to fit your operating system.

1. Download the latest cq-cli `dir` package from GitHub.
2. Extract the archive.
3. Copy all the files from the directory except `cq-cli`.
4. Past the files into either the `./addons/pythonscript/x11-64/lib` or `./addons/pythonscript/x11-64/DLL` directory. Do not overwrite any files that are already in the directory.

## Exporting