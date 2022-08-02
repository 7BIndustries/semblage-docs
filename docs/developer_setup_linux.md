# Developer Setup - Linux

## Introduction

Below are the steps that should produce a working Semblage environment from scratch. This guide will walk developers through that process, and will also explain the export process to get a Semblage package ready for distribution. These steps should be similar (but not exactly the same) on Windows, Mac OS and Linux. Please contribute to this guide if you develop primarily on Linux and have suggestions on how to make this guide better.

## Steps For Working Dev Environment

* Download and install [Godot 3.4.5](https://godotengine.org/download) or a newer 3.4.x version for 64-bit Linux.
* Clone the Semblage repo with `git clone --recurse-submodules https://github.com/7BIndustries/Semblage.git`.
* Run Godot and import the Semblage project file.
* Go to the AssetLib tab.
* Search for "pythonscript".
* Click on the _PythonScript_ plugin available from touilleMan.
* Click the _Download_ button in the dialog that comes up.
* One the download has completed, click the _Install..._ button.
* Leave everything at the default in the _Package Installer_ dialog and click the _Install_ button.
* You should eventually get a message that the package installed successfully and you can click the _OK_ button.
* Search the `AssetLib` for `gut`.
* Install the _Gut - Godot Unit Testing_ package from _bitwes_.
* Open a terminal and make sure you are in the root `Semblage` directory.
* Set `addons/pythonscript/x11-64/bin/python3.8` to be executable: `chmod +x addons/pythonscript/x11-64/bin/python3.8`
* Run `addons/pythonscript/x11-64/bin/python3.8 -m ensurepip`
* Run `addons/pythonscript/x11-64/bin/python3.8 -m pip install git+https://github.com/CadQuery/cadquery.git`
* Restart Godot and reopen the Semblage project.
* Semblage should now run and work properly, including exporting the project for distribution.

## Exporting

There is a GitHub Action that will build this package, but the instructions below cover doing it on your local computer. This process should be done on a Linux computer, and has been tested on Ubuntu 18.04. Please note that the first time that you attempt to export the project the export dialog will prompt you to install the templates. Follow the process in the Godot documentation to install the templates.

* From within Godot click `Project -> Export...`
* In the dialog that comes up click `Linux/X11 (Runnable)` under _Presets_
* Click the `Export Project` button
* Set an empty directory named `Semblage` to export the files to in _Path:_
* Make sure that the _File:_ field is set to `Semblage.x86_64`
* Uncheck _Export With Debug_ if it is checked
* Click the _Save_ button

The Linux export process is partly managed by a custom export plugin, and this can take awhile to run. It may make it seem like the export dialog has stalled, but it has not. Once the _Save a File_ dialog closes you can also close the _Export_ dialog and inspect the directory holding the new export.

Once the export has completed, two files within the export directory must be set to be executable (if they are not already). These files are `Semblage` and `Semblage.x86_64`. You can set them to be executable in the following way.

* chmod +x /path/to/Semblage/Semblage
* chmod +x /path/to/Semblage/Semblage.x86_64

## Testing an Exported Package

To test an exported package, double click `Semblage` in the export directory. The Semblage GUI should launch. In some Linux desktop environments you must configure the file manager to run text files that have been set as executable. Next, right click in the Semblage 3D view and add a _New Component_. All of the default settings are fine. Then right click again and add a box (under the 3D group). The default settings for this are fine too. If the box is rendered your release is valid, and can be packaged.

## Creating the Release Archive

Add the _Semblage_ directory to an archive named _Semblage_Linux_x86_64.tar.xz_. This archive can then be uploaded to a release.
