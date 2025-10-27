# Solidworks_DXF-Export-Tool
Sheet-metal export macro for batch export of Flat-patterns to DXF DWG. Supports Multi-Body export, export from .sldasm, autocorrects parts folded in flat-pattern config.

For those who do a lot of sheet-metal, you probably know exporting large quantities of flat patterns can take time. Before trying a paid service, I decided I would take a stab at writing a macro to handle batch exporting many files with many configurations. Ultimately, it turned into a saga. But I've been wanting to share it for a while now since I learned a lot on the SW forums in the process of making this, and I'm happy to be returning it in a new form to those who contributed with their sheet-metal VBA posts. Below you'll find the About doc that is part of the macro.

Uses:
-------------------------------------------------
- This export tool supports exporting all bodies in a multi-body sheet-metal sldprt.
- Batch export any configurations in a single sldprt file to DXF/DWG.
- Export a 'batch' of part files; Specify whether to export all configurations, or all
parent configurations only; Specify whether to export all bodies in each
configuration or the 1st (original) body in a configuration.
configuration body only.
- Automatically correct flattended states of configurations whose flat-pattern is
not unsuppressing all bends. Correcting bends can be run on part files for
export, or can be run on part files without exporting DXF/DWGs.

Single / Batch / Asembly:
-------------------------------------------------
- SINGLE exports the active part file. The user chooses configurations and
bodies to export.

- BATCH searches for all .SLDPRT files in the folder where the active document
resides. In the selection pane, check the desired parts for export. By default,
all parent configurations only are exported unless 'All' has been selected. By
default, default, only the 1st (or original) body is exported unless 'All' has
been selected.

- ASSEMBLY exports will export all unsuppressed sheet-metal parts in the active
assembly configuration; will not export the same configuration when duplicate
instances are found in the assembly.

Optional: Add the total configuration instance quantity found in the assembly
as a suffix in the exported DXF/DWG filename.

Optional: Add the total configuration instance quantity found in the assembly
as a configuration-specific property in the part-file.

- All export files are output to individual folders that then separate flat-patterns
into additional folders separated by Material and Thickness.

Setup:
-------------------------------------------------
- A single .SLDPRT/.SLDASM file must be open before running the export. The
macro will not proceed unless only 1 Solidworks file is open.
- Export file(s) must contain a Sheet-Metal body, or the export tool will skip over
that file. This is particularly useful for large assemblies that contain lots of
non-sheet metal bodies, such as hardware, weldments, surfaces...
- For Mapping file use, the 'settings' button will allow for direct access to, and
manipulation of, the DXF/DWG export system options. Changing these
settings will only be maintained for the duration of the export. Upon
completion of the export, the DXF/DWG export settings in the Solidworks
system options are returned to their original values.
- When making a Solidworks MACRO BUTTON, make sure to specify the method
from which to initiate the macro: mMain.Main

- CAUTION! Do not add or removed files/folders from the folder
where the export part(s)/assembly reside. Doing so may cause the program to
crash.

Troubleshooting:
-------------------------------------------------
- If Bend Correction is enabled and part does not flatten, check sldprt file for
errors or warnings. Correct all errors before re-running the tool.
- If Bend Correction is enabled and bend lines do not show, check sldprt file for
errors or warnings. Correct all before re-running the tool.

The tool has a lot options, with a lot of readme built-in, so hopefully using it is 
self-explanatory. I finished this sometime early 2021 and hadn't looked at it for a 
while up in until recently. I made a few changes per some feedback and then fixed 
and broke a few things, and now everything seem to run stable. If you find errors 
or have bugs, see the about. 

Thanks SS
