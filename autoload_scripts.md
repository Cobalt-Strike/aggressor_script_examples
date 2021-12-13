# Scripts can be automatically loaded in several ways

Method             | Description
-------------------|--
agscript           | allows for loading scripts outside the GUI
`include` function | Aggressor function that allow one script to load another
.aggressor.prop    | The aggressor config file will run saved scripts

## agscript

The agscript program (included with the Cobalt Strike Linux package) runs the headless Cobalt Strike client. 

Syntax to load script

```
./agscript [host] [port] [user] [password] [/path/to/script.cna]
```

https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/agressor_script.htm

## `include` function

The include function allow for one script to load another. 

## Note on scoping

Scoping is based on the first loaded script. This can cause variables to not function as expected. Test before using.

Example: init.cna

```
include(script_resource("submodule1.cna"));
include(script_resource("submodule2.cna"));

```

## .aggressor.prop

The .aggressor.prop file is the Cobalt Strike config file for the GUI. It can be found in the user's home directory.

Scripts added via the GUI will be added to this file. You can also edit the file directly before starting the CS GUI. This can be used to deploy a common set of scripts.

The option `cortana.scripts` contains the a `\!\!` separated list of full paths

Example of loading two scripts

```
cortana.scripts=/home/user/Development/aggressor_script_notes/misc_functions.cna\!\!/home/user/Development/aggressor_script_notes/data_models.cna
```
