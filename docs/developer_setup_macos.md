# Developer Setup - MacOS

## Introduction

Below are the steps that should produce a working Semblage environment from scratch. This guide will walk developers through that process, and will also explain the export process to get a Semblage package ready for distribution. These steps should be similar (but not exactly the same) on Windows, Mac OS and Linux. Please contribute to this guide if you develop primarily on MacOS and have suggestions on how to make this guide better.

## Prerequisites

Open a terminal and run the following commands.

* `xcode-select --install`
* `brew install python3 openssl zlib`

## Steps For Working Dev Environment

* Download [Godot 3.3.2](https://downloads.tuxfamily.org/godotengine/3.3.2/Godot_v3.3.2-stable_osx.universal.zip) for MacOS.
* Clone Semblage repo.
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
* Download the cq-cli package from [here](https://github.com/CadQuery/cq-cli/releases/download/v2.1.0/cq-cli-MacOS.zip).
* Unzip the contents of the cq-cli directory which are not directories into `Semblage/addons/pythonscript/osx-64/lib/python3.8/lib-dynload`.
* Download the zip file of the CadQuery repo from [here](https://github.com/CadQuery/cadquery/archive/refs/tags/2.1.zip).
* Copy the `cadquery-2.1/cadquery` directory to `Semblage/lib`.
* Delete the `Semblage/libs/exdxf` that was just copied. 
* Open a terminal window and make sure you are in the root `Semblage` directory.
* Run `chmod +x addons/pythonscript/osx-64/bin/python3.8`
* Run `addons/pythonscript/osx-64/bin/python3.8 -m ensurepip`
* Run `addons/pythonscript/osx-64/bin/python3.8 -m pip install typing_extensions`
* Run `addons/pythonscript/osx-64/bin/python3.8 -m pip install pyparsing`
* Run `addons/pythonscript/osx-64/bin/python3.8 -m pip install ezdxf`
* Run `addons/pythonscript/osx-64/bin/python3.8 -m pip install nptyping`
* Run `addons/pythonscript/osx-64/bin/python3.8 -m pip install scipy`
* Copy `typing_extensions.py` to `Semblage/libs` if Godot still complains about not being able to find the typing_extensions module.

## Exporting

Support for MacOS release packages has been dropped due to problems with not having the Python library signed. If someone is a MacOS user with a paid Appple developer account who wants to take on getting MacOS builds working again, please contact the development team. Below are the steps that should provide a working export package if application signing is possible with your developer account.

This process should be done on a MacOS computer, and has been tested on Mojave 10.14.6. Please note that the first time that you attempt to export the project the export dialog will prompt you to install the templates. Follow the process in the Godot documentation to install the templates.

* From within Godot click `Project -> Export...`
* In the dialog that comes up click `Mac OSX (Runnable)` under _Presets_
* Click the `Export Project` button
* Set an empty directory named `Semblage` to export the files to in _Path:_
* Make sure that the _File:_ field is set to `Semblage.zip`
* Uncheck _Export With Debug_ if it is checked
* Click the _Save_ button

The MacOS export process is partly managed by a custom export plugin, and this can take awhile to run. It may make it seem like the export dialog has stalled, but it has not. Once the _Save a File_ dialog closes you can also close the _Export_ dialog and inspect the directory holding the new export.

Once the export has completed, one clean-up action needs to be completed.

* Expand the Semblage.zip file into the root Semblage export directory.
* Delete the Semblage.zip file.

## Testing an Exported Package

To test an exported package, double click `Semblage` in the export directory. The Semblage GUI should launch. Next, right click and add a _New Component_. All of the default settings are fine. Then right click again and add a box (under the 3D group). The default settings for this are fine too. If the box is rendered your release is valid, and can be packaged.

## Creating the Release Archive

Add the _Semblage_ directory to an archive named _Semblage_MacOS.zip_. This archive can then be uploaded to a release.