# Introduction

Semblage is an open source 3D CAD application that seeks to blend the GUI (Graphical User Interface) and programmatic CAD worlds. To get an idea of where Semblage is headed in the future, have a look at the [roadmap](roadmap.md). Semblage needs a firm foundation first though, with stable core functionality and a good user experience in mind. That is the current focus of this project.

## Features

* 2D sketches with preview
* 3D operations (extrude, cut, etc)
* Export for manufacturing: STEP, STL, SVG and DXF
* Underlying file format is a [CadQuery](https://cadquery.readthedocs.io/en/latest/index.html) Python-based programmatic CAD (a.k.a. CodeCAD) script

## Goals

The high-level goals of Semblage are as follows.

* Focused on desktop manufacturing, hobbyists, makerspaces, etc.
* Mouse driven as much as possible, doing more with mouse interaction as time progresses while trying to preserve the depth of control the user has with scripting.
* Keep the highly parametric nature of CadQuery available through the user interface.
* Provide the user with the full depth of scripted CAD when (and if) they want/need it.
* Be able to export to formats that are useful for desktop and makerspace manufacturing, such as 3D printing, laser cutting, CNC routing, vinyl cutting, etc.
* Be able to generate mechanical drawings and export them to industry standard formats (DXF, SVG).
* Generated CadQuery code should be portable and standard, and capable of being run from the command line.

## Terms

* ***Component*** - General term for geometry that can be a 2D sketch, a face, a solid, or (eventually) an assembly. Components to be used in combination as in the case of a sweep operation, or nested within each other to build assemblies (eventually).
* ***CadQuery*** - A Python based CAD scripting API that is at the heart of Semblage. [CadQuery](https://cadquery.readthedocs.io/en/latest/index.html) is good at capturing design intent with features like selectors, and is capable of creating very powerful, highly parametric design scripts.
* ***Script*** - A collection of statements that are executed when needed, rather than compiled into a binary program. Semblage uses the CadQuery CAD scripting API to generate models. Each Semblage component is simply a CadQuery Python script. This has multiple advantages, including making it easier to track CAD models within a code versioning system like git. It can bring security challenges with it as well, which is why Semblage will prompt you with a warning if the component script you are opening imports anything more than the standard CadQuery packages.
* ***CodeCAD*** - Interchangeable with the phrase _programmatic CAD_, which describes CAD objects that are specified by a script rather than by mouse interaction.

## What To Expect

Semblage is in alpha at this time, so core features may be missing or broken. Use at your own risk and remember to save often. There is a Ctrl+S keyboard shortcut for save to make it easier to save your work frequently. Also, back up your component files at critical points in the design process.

The operations available in Semblage are annotated with documentation within the UI, and have been derived from their CadQuery counterparts. The [CadQuery documentation](https://cadquery.readthedocs.io/en/latest/) can be useful for finding more detail on Semblage operations. Understanding CadQuery will open additional design possibilities by helping to tap into the scripting power at the core of Semblage.

Here is a list of currently missing features that users may find limiting or confusing. Each item in this list can be read with a "not yet" added to it. The goal is to implement all of these missing features over time.

* Features of the model (edges, vertices, faces) cannot be selected yet.
* Selector definition is not mouse-driven at this time. Selectors must be created manually. Adding mouse interaction to infer selectors will be the focus of a future release.
* 2D sketching with preview is partially working, but is not mouse driven at this time.
* 2D sketching does not include constraints.
* 3D assembly is not available yet.
* Some export formats (notably AMF) are not available yet.

A good next step from here is to continue to the [Installation](installation.md) documentation.
