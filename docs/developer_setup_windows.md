# Developer Setup - Windows

## Introduction

Below are the steps that should produce a working Semblage environment from scratch. This guide will walk developers through that process, and will also explain the export process to get a Semblage package ready for distribution. These steps should be similar (but not exactly the same) on Windows, Mac OS and Linux. Please contribute to this guide if you develop primarily on Windows and have suggestions on how to make this guide better.

## Prerequisites

* Python 3.8+
* Visual Studio 2017 or 2019 (2019 is preferred)

## Steps For Working Dev Environment

* Download [Godot 3.4.5](https://godotengine.org/download) or newer 3.4.x version for Windows.
* Clone Semblage repo with `git clone --recurse-submodules https://github.com/7BIndustries/Semblage.git`.
* Run Godot and open the Semblage project file.
* Go to the AssetLib tab.
* Search for "pythonscript".
* Click on the _PythonScript_ plugin available from touilleMan.
* Click the _Download_ button in the dialog that comes up.
* One the download has completed, click the _Install..._ button.
* Leave everything at the default in the _Package Installer_ dialog and click the _Install_ button.
* You should eventually get a message that the package installed successfully and you can click the _OK_ button.
* Search the `AssetLib` for `gut`.
* Install the `Gut - Godot Unit Testing` package from _bitwes_.
* Open a command line and make sure you are in the root `Semblage` directory.
* Run `.\addons\pythonscript\windows-64\python.exe -m ensurepip`
* Run `.\addons\pythonscript\windows-64\python.exe -m pip install --pre git+https://github.com/CadQuery/cadquery.git`
* Restart Godot and reopen the Semblage project.
* Semblage should now run and work properly, including exporting the project for distribution.

## Exporting

The cross-platform export does not currently work for the Windows version of Semblage due to the Python plugin. This process should be done on a Windows computer, and has been tested on Windows 10. Please note that the first time that you attempt to export the project the export dialog will prompt you to install the templates. Follow the process in the Godot documentation to install the templates.

* From within Godot click `Project -> Export...`
* In the dialog that comes up click `Windows Desktop (Runnable)` under _Presets_
* Click the `Export Project` button
* Set an empty directory named `Semblage` to export the files to in _Path:_
* Make sure that the _File:_ field is set to `Semblage.exe`
* Uncheck _Export With Debug_ if it is checked
* Click the _Save_ button

The Windows export process is partly managed by a custom export plugin, and this can take awhile to run. It may make it seem like the export dialog has stalled, but it has not. Once the _Save a File_ dialog closes you can also close the _Export_ dialog and inspect the directory holding the new export.

Due to the nature of how the Python plugin works on Windows, a copy of the Semblage repo's main structure must be made in the export directory. This carries with it some files and directories that are not needed and can be deleted. This manual clean up step helps declutter the zip file for end users. Below is a list of those files/directories that can and should be removed before uploading.

* .git
* .github
* __pycache__
* .gitignore
* .gitmodules
* Semblage.pck

## Testing an Exported Package

To test an exported package, double click Semblage.exe. The Semblage GUI should launch. Next, right click in the Semblage 3D view and add a _New Component_. All of the default settings are fine. Then right click again and add a box (under the 3D group). The default settings for this are fine too. If the box is rendered your release is valid, and can be packaged.

## Creating the Release Archive

Add the _Semblage_ directory to an archive named _Semblage_Windows_64.zip_. This archive can then be uploaded to a release.
