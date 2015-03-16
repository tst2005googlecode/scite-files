# Introduction #

F# is a cousin language of OCaml, therefore its syntax can be derived from the ocaml.properties file. Below I have reported a tentative extension of the original file.

# Details #

```
filter.ocaml=OCaml (ml mli)|*.ml;*.mli|
filter.fs=F# (fsx fsscript fs fsi)|*.fsx;*.fsscript;*.fs;*.fsi|

file.patterns.ml=*.ml;*.mli
file.patterns.fs=*.fsx;*.fs;*.fsi;*.fsscript
file.patterns.all=file.patterns.ml;file.patterns.fs

lexer.$(file.patterns.ml)=caml
lexer.$(file.patterns.fs)=caml

keywordclass.ocaml= and as assert asr begin class closed \
constraint do done downto else end exception external false for fun \
function functor if in include inherit land lazy let lor lsl lsrlxor match method \
mod module mutable new of open or parser private rec sig struct then to true \
try type val virtual when while with
keywords.$(file.patterns.ml)=$(keywordclass.ocaml)

keywordclass.fs=abstract and as assert base begin class default delegate do done downcast downto elif else end exception extern false finally for fun function global if in inherit inline interface internal lazy let let! match member module mutable namespace new not null of open or override private public rec return return! select static struct then to true try type upcast use use! val void when while with yield yield!
keywords.$(file.patterns.fs)=$(keywordclass.fs)

statement.indent.*.ml=3 :
statement.end.*.ml=
statement.lookback.*.ml=0
block.start.*.ml=in then begin
block.end.*.ml=end done

statement.indent.*.fs=4 :
statement.end.*.fs=
statement.lookback.*.fs=0
block.start.*.fs=in then begin
block.end.*.fs=end done

tab.timmy.whinge.level=1

fold.comment.ocaml=1
#fold.quotes.ocaml=1

comment.stream.start.ocaml=(*
comment.stream.end.ocaml=*)
comment.box.start.ocaml=(*
comment.box.middle.ocaml=*
comment.box.end.ocaml=*)

comment.stream.start.fs=/*
comment.stream.end.fs=*/
comment.box.start.fs=/*
comment.box.middle.fs=*
comment.box.end.fs=*/

comment.block.fs=//~

# ocaml styles
# White space
style.ocaml.0=fore:#808080
# Comment
style.ocaml.1=fore:#007F00,$(font.comment)
# Number
style.ocaml.2=fore:#007F7F
# String
style.ocaml.3=fore:#7F007F,$(font.monospace)
# Single quoted string
style.ocaml.4=fore:#7F007F,$(font.monospace)
# Keyword
style.ocaml.5=fore:#00007F,bold
# Triple quotes
style.ocaml.6=fore:#7F0000
# Triple double quotes
style.ocaml.7=fore:#7F0000
# Class name definition
style.ocaml.8=fore:#0000FF,bold
# Function or method name definition
style.ocaml.9=fore:#007F7F,bold
# Operators
style.ocaml.10=bold
# Identifiers
style.ocaml.11=
# Comment-blocks
style.ocaml.12=fore:#7F7F7F
# End of line where string is not closed
style.ocaml.13=fore:#000000,$(font.monospace),back:#E0C0E0,eolfilled
# Matched Operators
style.ocaml.34=fore:#0000FF,bold
style.ocaml.35=fore:#FF0000,bold
# Braces are only matched in operator style
braces.ocaml.style=10

if PLAT_WIN
	command.go.*.ml=ocamlw -u $(FileNameExt)
	command.go.subsystem.*.ml=1
	command.go.*.mlw=ocamlw -u $(FileNameExt)
	command.go.subsystem.*.mlw=1
	
	command.go.*.fsx=fsi $(FileNameExt)
	command.go.subsystem.*.fsx=1
	command.build.*.fs=fsc $(FileNameExt)
	command.go.*.fs=$(FileName)
	command.go.subsystem.*.fs=1
	
if PLAT_GTK
	command.go.*.ml=ocaml -u $(FileNameExt)

command.name.1.*.ml=Syntax Check
command.1.*.ml=ocaml -c "import ml_compile; ml_compile.compile(r'$(FilePath)')"
```