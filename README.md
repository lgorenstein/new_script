# new_script
A generator for new Bash scripts

This program is a tool to generate basic skeleton template for new Bash
scripts.  It automates creation of a general script structure (header,
handful of utility functions, help text, command line arguments parser,
etc), which you could then edit and add meat onto provided bones.  Advanced
functionality and CLI parsing is something that many home-grown scripts
~eventually~ need (even if they originally started as simple one-liners
without it), so using this generator greatly simplify development.

The original `new_script` tool was written by William Shotts in 2012, and
is available at https://linuxcommand.org/lc3_new_script.php  I ran across
it in 2013 or 2014, and immediately fell in love.  As I was gradually
adding features I wanted over the years, I may have somewhat marred the
elegance and beauty of Mr. Shotts' original code.  My branch no longer
looks pretty... but it does have a few extra bells and whistles.  At the
very least, it attempts to keep the generated template clean. 

## Installation
The script is self sufficient - just copy it anywhere in your $PATH.
The simplistic configuration file can be placed into `$HOME/new_scriptrc`
(see code to understand what can or can not be configured).

## Usage
```bash
new_script [-h|--help ] [-q|--quiet] [-s|--root] [-t|--tab] [script]

Options:

-q, --quiet   Quiet mode. No prompting. Outputs default script.
-s, --root    Output script requires root privileges to run.
-t, --tab     Output indentation by tabs (as opposed to default '   ').
-h, --help    Display this help message and exit.
```

Then follow prompts for desired features and future command line options
for your new script `script`!

For example:
```bash
$ new_script example.sh
Enter purpose of script: This is a demo
Include GPL license header [y/N]? n
Does this script require superuser privileges [y/N]? n
Indent by tabs instead of by '   '? [y/N]? n
Does this script support command-line options [y/N]? y

Option 1:
Enter option letter [a-z] (Enter to end) > l
Description of option -------------------> Specify sample length
Enter long alternate name (optional) ----> length
Enter option argument variable (if any) -> LENGTH

Option 2:
Enter option letter [a-z] (Enter to end) >

$ ls -l example.sh
-rwxr-xr-x 1 user group 7259 Mar 14 02:27 example.sh*
```

Note that a handful of default options (`--help`, `--quiet`, `--verbose`,
and `--version`) are generateded automatically, and do not have to be
specified by hand.
