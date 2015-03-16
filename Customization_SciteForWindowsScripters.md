# SciTE for Windows Scripters #

(This is a mirror saved from remotenetworktechnology.com which is now dead.)

I've recently started using SciTE, a testbed text editor built around Scintilla, as my primary tool for scripting work.  You can find out more about the editor and the core tool from the SciTE/Scintilla home page.

Note that SciTE and Scintilla are separate things.  Scintilla is a component designed to aid in editing source code; SciTE means Scintilla based Text Editor; it was originally a demo for the Scintilla component, but turned out to be much more useful and popular than your average "Hello, World" demonstration.

## Why Use SciTE For Windows Scripting? ##

It's a matter of preference; and SciTE provides features which are commensurate with many commercial text editors and well-advanced beyond them in others.

The critical factor for me was the exposure of many points of control within SciTE; scripting is a specialty category, and few text editors cater to it specifically (although Scintilla specifically seems to have evolved from Neil Hodgson's desire to improve PythonWin text editing - Scintilla is definitely "script-aware") .  SciTE does NOT cater to scripters; it DOES give you easy access to customize everything, which is even better.

If you are already basically comfortable with scripting and need a high-performance tool, this is definitely worth a look.

SciTE features:

<ul><li>fully customizable syntax highlighting (of course).<br>
</li><li>Text folding for structures, procedures, and classes.<br>
</li><li>a customizable tools menu which supports document-sensitive configuration and a good set of support macros<br>
</li><li>Language-specific highlighting and folding for structured documents such as WSF and WSC files.<br>
</li><li>Configurable execution subsystems for tools - you can shell execute, run a console command internally and capture output, or run it externally, for example.<br>
</li><li>line numbering, with configurable properties<br>
</li><li>A host of capabilities you won't value until you see them in action.  The richness of the config files can look overwhelming at first, but the flat Unixish structure makes it easy to home in on what you want to change, and the SciTEDoc.html file accompanying it explains in detail what the settings mean.</li></ul>


SciTE is not a "perfect" tool, of course; its commitment to creating a cross-platform core and the limited time of developers who are providing a tool that costs nothing to start using means that there are some things you simply don't have without extra effort of your own.  For example, context menuing in vanilla SciTE is very basic, providing only standard cut-copy-paste-select (but including undo/redo); the multi-document interface depends on tabbing, since only one document is displayed at a time.


The advanced configurability make compensating for internal limitations fairly easy; and in fact the extensible structure of SciTE makes it possible to use a superior external tool for a specific job - a much better situation than being stuck with a hard-wired internal  tool (the object browser in VB and Microsoft Office comes to mind).


All in all, given some time to work with it, this is probably the best vehicle available for a personalized editing environment.


## WSH Scripts for SciTE ##

Since I tend to write my own tools for almost everything I do with scripting, I spent a few minutes adapting the primary ones I use to work with SciTE. Below are several of the adaptations I have made.

I make no claim that these are in any way complete at this point; I wrote them for my own use after about 3 days experience with SciTE.  I am providing them as a potential starting point for other people using SciTE.

Also note that some people may find that Filerx is a useful tool for adding macroing features to SciTE; a few of the script tools below may be more useful there.

## WSH-Related SciTE Properties Files ##

<font size='3'><a href='http://scite-files.googlecode.com/svn-history/trunk/extras/Windows_scripting_scripts.zip'>Download files mentioned in this article</a></font>

SciTE/vbscript.properties

Extended keywords for VBScript.

SciTE/vbscript\_abbrev.properties

Clip text abbreviations for SciTE; includes my most frequently reused functions, subroutines, and code blocks.

SciTE/ws.properties

A preliminary version of a parser for embedded highlighting of WSF and WSC files.

SciTE/demo.properties

## SciTE Helper Scripts ##

<font size='3'><a href='http://scite-files.googlecode.com/svn-history/trunk/extras/Windows_scripting_scripts.zip'>Download files mentioned in this article</a></font>

SciTE/Scitevbp.vbs.txt

Works via drag-and-drop or as a tool.  Given a VBP file as a target, will parse it for all member files and load them in SciTE. In SciTE, if using an opened VBP as the target set the command target to something like

cscript <path-to-Scitevbp.vbs>  "$(FilePath)"

SciTE/WordCheck.vbs.txt

A script which allows running spell checks on documents in SciTE using the Word Spelling and Grammar checker.

Wscript <path-to-Wordcheck.vbs>  "$(FilePath)"

SciTE/mskb.vbs.txt

Script to retrieve the raw text from an MSKB article; can be used by highlighting an embedded Q article number in the active document. This will "clean"  a Q-number, removing everything but the actual numbers from the string first, so if you have an old URL with embedded slashes or grab white space or characters around the number it doesn't matter.   For in-SciTE capture, use a command like this:

cscript <path-to-Scitevbp.vbs>  $(CurrentSelection)

and set the subsystem to 0.

SciTE/GetXml.vbs.txt

Similar to the above, but will retrieve the source HTML of a selected URL via the Microsoft.XMLHTTP object.  As above, for in-SciTE capture, use a command like this:

cscript <path-to-Scitevbp.vbs>  $(CurrentSelection)

and set the subsystem to 0.

SciTE/ChangeScriptingEditor.vbs.txt

This is an adaptation of Jim Warrington's script for modifying the default Windows editor for scripts.  It has been customized to point to my copy of SciTE; you will need to edit the embedded path to use this, but it definitely speeds up the process of setting default editors as you choose.