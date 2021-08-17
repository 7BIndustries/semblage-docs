# Codebase Tour

Below is a listing of different files and directories within the codebase, along with what their significance is. The hope is that this will aid new developers in getting up to speed more quickly when starting with Semblage.

## GUI

* `GUI.tscn` - The "Main Scene", this is the scene that is loaded when the application starts up.
* `GUI.gd` - Script attached to GUI.tscn, and is the main code entry point to the app. Start here to see where the rest of the app branches out to. This is attached to the main Control node at the top of the scene tree in the Godot GUI.
* `ActionPopupPanel.gd` - The GDScript for the Operations dialog. The dialog was originally named "Actions", but "Operations" made more sense and there are some places like this where the naming has not been changed. When the user right clicks on the 3D view, this is the code that is run to display the Operations dialog. The matching nodes can be found in the scene tree under the "ActionPopupPanel" WindowDialog node. This dialog will dynamically load controls based on Triggers.gd, which is described next.
* `Triggers.gd` - Contains a map of operations and controls. When an operation is selected in the Operations dialog, this is used to find out which control to load. When an operation in the history list is double clicked for editing, this map is consulted to figure out which control to load so that the settings can be altered.
* `controls/` - Directory that holds the controls that are dynamically loaded into the Operations dialog (ActionPopupPanel). The `action.control` key in Triggers.gd contains a path to one of these controls.
* `controls/Common.gd` - Contains functions that are common to a wide range of controls so that this code is not duplicated in each individual control.
* `ContextHandler.gd` - Utility code that helps Semblage figure out what comes next based on the current CadQuery script's code (the context). Passing the code string to the functions in this class will return various things that the GUI uses to decide what to display to the user next.
* `lib/` - Contains the CadQuery library and the interface file that is used by Godot to make Python calls to CadQuery's CQGI system.
* `lib/cqgi_interface.py` - Python script that is Godot's window into CadQuery's world. Script text is passed to the functions to be built or evaluated. If the object is being built, a JSON string is passed back. There may be experiments at some point in removing the JSON and just having the Python calls add meshes directly to the 3D view. Searching for "cqgi" in either GUI.gd or ActionPopupPanel.gd will show where/how this interface is called.
* `assets/` - Directory containing fonts, the icons for the application, and a few outdated sample CadQuery scripts.
* `cameras/OrbitCamera.gd` - Contains the code for the orbit camera used in both the 3D view and the axis indicator.
* `AboutDialog.gd` - Code for the About dialog which contains sponsor, contributor and version information.
* `AddParameterDialog.gd` - Code for the popup that allows a user to create a new parameter. Shown when the user clicks the plus button on the _Parameters_ list. These parameters are added as variables to the component script when a render is requested. Parameters can contain other parameter names and formulas.
* `Canvas2D.gd` - Code that allows 2D objects to be drawn as a preview. Curves are discretized into line segments and those are drawn by this canvas code.
* `DocumentTabs.gd` - The document tab that holds the 3D view. It is undecided yet whether there will be multiple document tabs allowed, or whether a component will be selected to make it the focus for editing in the existing 3D view, removing the need to have multiple tabs.
* `ExportDXFDialog.gd` - Code to control the dialog to export DXF files.
* `ExportSVGDialog.gd` - Code to control the dialog to export SVG files.
* `FileSystem.gd` - Custom utility class to help with some Semblage-specific interactions with the filesystem.
* `LinAlg.gd` - Class holding some linear algebra related functions for things like finding the distance between vectors.
* `Meshes.gd` - Even though CadQuery is built on a b-rep CAD kernel, the objects in the 3D view are displayed as 3D meshes in Godot's 3D viewport. This class holds functions for creating and manipulating those meshes. For instance, when a workplane is first added to the component, this is where the workplane visualization mesh is generated.
* `OmniLight.gd` - Custom Godot omni light that follows the orbit camera's rotation and translation. This was done to improve the lighting of the 3D objects as the camera rotates.
* `Security.gd` - Right now this code is only used to check if a script is trying to import more modules than is needed to run CadQuery. It is an attempt to cut down on malicious CAD scripts, and more advanced security checks will likely be added to this in the future.

## Infrastructure

* `addons/cadquery_export/` - Plugin that automates some extra steps in exporting the Semblage project for release. This is required because of the way the Python plugin and the OCP dependency interact.
* `addons/gut/` - GUT is the unit testing framework that Semblage uses. To be able to run the test suite locally this must be installed. The continuous integration configuration can be consulted on the best way to run the tests.
* `addons/pythonscript/` - Plugin that enables the Python subsystem that CadQuery runs on. Having this plugin is necessary, but has greatly complicated setup and distribution of Semblage.
* `pythonscript.gdnlib` - A Godot GDNative library related to the pythonscript plugin.
* `scripts/` - Directory containing the launcher shell script for the Linux version. This shell script is copied by the export plugin.
* `samples/` - Directory which contains sample scripts that are mainly used in the unit tests.
* `tests/` - Directory containing the unit tests for Semblage. A single test can be run by name with the form `LD_LIBRARY_PATH=$PWD/lib godot -d -s --path ./project addons/gut/gut_cmdln.gd -gdir=res://tests -gtest=./tests/actions_dialog/test_main_dialog.gd -gunit_test_name=test_selector_button`. All tests can be run with `LD_LIBRARY_PATH=$PWD/lib godot -d -s --path ./project addons/gut/gut_cmdln.gd -gdir=res://tests -ginclude_subdirs`.
* `translations.ods` - Open document spreadsheet, and the source file for the translations for the Semblage user interface. Each column contains a language, although only English has been added at this point. Once updated, this file has to be saved in CSV (comma delimited) format so that it can be imported and used by Godot. This can be opened in LibreOffice or OpenOffice, but should not be edited in Microsoft Office as it does non-standard things with the CSV export.
* `translations.csv` - The exported version of `translations.ods` that Godot can import.
