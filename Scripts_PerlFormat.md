The following was taken from Serge Baranov's SciTE package.
To install these scripts, first put the following information in SciTEGlobal.properties or SciTEUser.properties:
```
 command.name.20.*=Reformat
  command.20.*=perl $(SciteDefaultHome)\tools\formatall.pl $(SciteDefaultHome)\tools $(FilePath)
  command.quiet.20.*=1
  command.is.filter.20.*=1
  command.save.before.20.*=1
  command.shortcut.20.*=Ctrl+Alt+L
  
  command.name.9.*=Strip trailing spaces
  command.9.*=perl $(SciteDefaultHome)\tools\stripspace.pl $(FilePath)
  command.quiet.9.*=1
  command.is.filter.9.*=1
  command.save.before.9.*=1
  
  command.name.8.*=Strip last empty lines
  command.8.*=perl $(SciteDefaultHome)\tools\striplines.pl $(FilePath)
  command.quiet.8.*=1
  command.is.filter.8.*=1
  command.save.before.8.*=1
```

Then, create the following files in a folder "tools" inside the SciTE directory.

formatall.pl
```
#!/usr/bin/perl
`perl $ARGV[0]\\stripspace.pl $ARGV[1]`;
`perl $ARGV[0]\\striplines.pl $ARGV[1]`;
`perl $ARGV[0]\\tabs2spaces.pl -f $ARGV[1]`;
exit;
```


stripspace.pl
```
#!/usr/bin/perl

open(IN, $ARGV[0]);
@buff = <IN>;
close(IN);

open(OUT, ">$ARGV[0]");
foreach(@buff) {
  s/\s+$/\n/;
  print OUT "$_";
}
close(OUT);
exit;
```


striplines.pl
```
#!/usr/bin/perl
my $blank_lines = 0;

open(IN, $ARGV[0]);
@buff = <IN>;
close(IN);

open(OUT, ">$ARGV[0]");
foreach(@buff) {
  s/\s+$//;
  unless($_) {
    $blank_lines++;
    next;
  }
  print OUT "\n" x $blank_lines if $blank_lines;
  $blank_lines = 0;
  print OUT "$_\n";
}
close(OUT);
exit;
```

Now, assuming Perl is installed, you should be able to run these scripts.