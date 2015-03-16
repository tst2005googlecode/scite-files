# Introduction #

By using the Perl script reported here you can maintain more easily your abbreviations.


# Details #

You can customize the abbreviations associated to a given _language_ by adding the following line in the _language_.properties file:

abbreviations.$(file.patterns._ext_)=$(SciteDefaultHome)/_language_.abbrev

The file _language_.abbrev has the following format

```
shortcut1=code1
shortcut2=code2
...
```

each code snippet must reside in a single line, therefore the newlines must be written as "\n" and this fact makes abbrev files rather cluttered to maintain. To ease the creation of such a file I have written this simple Perl script:

```
#!/usr/bin/perl

use diagnostics;
use strict;

my $name = $ARGV[0];
my $file = $name . ".txt";
my $file1 = $name . ".abbrev";
open(INPUT, $file) || die("Cannot read '$file'!");
open(OUTPUT, ">" . $file1) || die("Cannot write '$file1'!");

my $txt = <INPUT>;
chomp($txt);
while (<INPUT>) {
	chomp;
	if ($_ eq '------------------------------------------------------------------------------') {
		print OUTPUT $txt if ($txt ne '');
		$_ = <INPUT>;
		chomp;
		$txt = "\n$_";
	}
	else {
		$txt .= $_ . '\n';
	}
}

close(OUTPUT);
close(INPUT);
```

This script allows you to start from a text like the following saved in a file named _language_.txt:

```
------------------------------------------------------------------------------
ec=# end class Name
------------------------------------------------------------------------------
et=# end try
------------------------------------------------------------------------------
GetOpt parameters=
import argparse

parser = argparse.ArgumentParser(description='...')
# nargs: *= [0,), + =(0,), ?=[0,1]
parser.add_argument('positional_param', metavar='N', type=int, nargs='+',
                   help='...')
parser.add_argument('--named_parameter', dest='dest_var_name', action='store_const',
                   const=value_to_store, default=default_value,
                   help='...')
parser.add_argument('--flag', dest='dest_var_name', action='store_true', required=True,                   
                   help='...')
						 
args = parser.parse_args()
print args.dest_var_name
```

and, by invoking the script "on it" (e.g.: ./create\_abbrev.pl _language_), to obtain a ready-to-use _language_.abbrev:

```
ec=# end class Name
et=# end try
GetOpt parameters=import argparse\n\nparser = argparse.ArgumentParser(description='...')\n# nargs: *= [0,), + =(0,), ?=[0,1]\nparser.add_argument('positional_param', metavar='N', type=int, nargs='+',\n                   help='...')\nparser.add_argument('--named_parameter', dest='dest_var_name', action='store_const',\n                   const=value_to_store, default=default_value,\n                   help='...')\nparser.add_argument('--flag', dest='dest_var_name', action='store_true', required=True,                   \n                   help='...')\n						 \nargs = parser.parse_args()\nprint args.dest_var_name\n
```

Notice that:
  1. the dashes which separate the various abbreviations must be exactly as in the example (alternatively, simply change the script accordingly);
  1. if you want to use a pipe character ("|") you have to double it ("||"), since the single pipe is used by Scite to denote the cursor position.

Once the abbrev file has been saved in the Scite directory, the abbreviations can be expanded using the menu command Edit->Expand Abbreviation (CTRL+B); they can also be listed using Edit->Insert Abbreviation (CTRL+SHIFT+R).