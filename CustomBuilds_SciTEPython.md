# SciTE Python Extension #

Ben Fisher, 2011.
scitewiki@gmail.com

You can now write plugins and scripts in Python to customize SciTE.
You have access to the powerful standard library of Python.

## Download ##
Win32:
<a href='http://scite-files.googlecode.com/svn-history/trunk/custom/scite_python_extend/0.5/scite_python_extend_0_5_win32.zip'>SciTE 2.25 with Python</a> Beta, v0.5. (A Python installation is not needed.)



## Documentation ##
Refer to the readme.txt and scite\_extend\_doc.txt files that come with the distribution.

Some unit tests can be found in <a href='http://scite-files.googlecode.com/svn-history/trunk/custom/scite_python_extend/0.5/scite_extend_tests.py'>scite_extend_tests.py</a>. If this file is placed in the scite directory, by default, one can press Ctrl-1, Ctrl-2, and other commands to run tests.

This is a beta release; there are some known issues listed in the readme, feedback is welcome.

## Building from source ##
The gcc makefile has not yet been updated, so vc compiler needed.
Windows:

  1. Download the source for SciTE 2.25.
  1. Apply <a href='http://scite-files.googlecode.com/svn-history/trunk/custom/scite_python_extend/0.5/scite_python_extend.patch'>this patch</a>.
  1. Copy <a href='http://scite-files.googlecode.com/svn-history/trunk/custom/scite_python_extend/0.5/scite_python_extend_patchwin32.zip'>these files</a> into the appropriate directories.
  1. Build SciTE (nmake -f scintilla.mak, and then nmake -f scite.mak)

To build without any Python support, define NO\_PYTHON on the command line.

Gtk:
No instructions yet.

## Why ##
Python has more control over starting processes than Lua, for tasks like starting processes in a console and monitoring stdout. It also has a full standard library (components loaded on demand); I have found use for Python's html processing, xml, and ftp capabilities. Python might also be more familiar to people than Lua.

Thanks to Remi Gillig for sharing his Ruby extension, which was a useful resource.