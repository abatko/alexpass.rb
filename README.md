A Ruby program for generating [Alexpass] passwords from the command line

Example
--------

    $ alexpass.rb 
    nF7zHTNrjtYRmxod

Dependencies
------------

    require 'alexpass' # for actually generating the Alexpass passwords
    require 'optparse' # for command-line options parsing
    require 'yaml'     # for loading the YAML configuration file, if present

Setup
-----

 * `gem install alexpass`
 * `gem install optparse yaml` # the dependencies
 * download this Ruby script (`alexpass.rb`)
 * `mv ~/Downloads/alexpass.rb ~/bin/` # place this script in a suitable directory
 * `chmod u+x ~/bin/alexpass.rb` # give yourself permission to execute this script

Command-line Options
--------------------

    Usage: alexpass.rb [options]
        -l, --length [INTEGER>0]         Password length
        -m, --memorizable [true|false]   Use the memorizable pattern or not
        -p, --permutations [vvv]         Show permutation size; verbosity increases with v's
        -s, --switches                   Show password switches
        -h, --help                       Show this message

Configuration
-------------

### Program defaults

The program itself comes with the following defaults:

    options[:length] = 8
    options[:memorizable] = true
    options[:permutations] = false
    options[:switches] = false

### File override

Overrides program defaults.

    cat ~/.alexpass.yaml 
    :length: 16
    :memorizable: false

### Command-line super override

Overrides everything above. See *Command-line Options* above.

Examples
--------

These examples assume `alexpass.rb` is executable and in a directory in PATH, and the above mentioned *Configuration* section is in effect.

    $ alexpass.rb 
    nF7zHTNrjtYRmxod

    $ alexpass.rb -p
    oDKfhfYznFN3j4Nv
    2,869,959,681,148,181,529,600 permutations

    $ alexpass.rb --length 8 --memorizable true
    kSU5yx9e

    $ alexpass.rb -l8 -mt -pvvv -s
    jXJ3oc7z
    sample sets:
    ["y", "u", "i", "o", "p", "h", "j", "k", "n", "m"]
    ["Q", "W", "E", "R", "T", "A", "S", "D", "F", "G", "Z", "X", "C", "V", "B"]
    ["Y", "U", "P", "H", "J", "K", "L", "N", "M"]
    ["2", "3", "4", "5"]
    ["y", "u", "i", "o", "p", "h", "j", "k", "n", "m"]
    ["q", "w", "e", "r", "t", "a", "s", "d", "f", "g", "z", "x", "c", "v"]
    ["7", "8", "9"]
    ["q", "w", "e", "r", "t", "a", "s", "d", "f", "g", "z", "x", "c", "v"]
    10 * 15 * 9 * 4 * 10 * 14 * 3 * 14 permutations
    31,752,000 permutations
    --length 8 --memorizable true

