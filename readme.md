# Aggressor Script 

**Aggressor Script** is Cobalt Strike’s built-in scripting language. It is the preferred way to add features to Cobalt Strike, override existing behaviors (kits take advantage of this), and automate your engagements.

[Cobalt Strike](https://www.cobaltstrike.com) also ships with a headless client, ```agscript```, that connects to a Team Server and hosts an Aggressor Script for you. This client is designed for long-running bots. Common uses of headless Aggressor Scripts is to force DNS beacons to “check in” or notify an operator, via a text or email, that they have a new session.

## Examples
[This repository](https://github.com/Cobalt-Strike/aggressor_script_examples) contains tips, tricks, and examples of aggressor script functions. The intent is to share bite size examples that can be used in other scripts.

Item                     | Description
-------------------------|--------------------------
[data_models.cna](https://github.com/Cobalt-Strike/aggressor_script_examples/blob/main/data_models.cna)          | example of interating with and extracting data from the Cobalt Strike data models
[random_string.cna](https://github.com/Cobalt-Strike/aggressor_script_examples/blob/main/random_string.cna)        | functions to generate random data (i.e., random string generator)

## Scripts automatic load

Method             | Description
-------------------|--
agscript           | allows for loading scripts outside the GUI
`include` function | Aggressor function that allow one script to load another
.aggressor.prop    | The aggressor config file will run saved scripts

### agscript

The agscript program (included with the Cobalt Strike Linux package) runs the headless Cobalt Strike client. 

Syntax to load script:

```bash
./agscript [host] [port] [user] [password] [/path/to/script.cna]
```

[Read More](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/agressor_script.htm)

### `include` function

The include function allow for one script to load another. 

### Note on scoping

Scoping is based on the first loaded script. This can cause variables to not function as expected. Test before using.

Example: init.cna

```perl
include(script_resource("submodule1.cna"));
include(script_resource("submodule2.cna"));
```

### .aggressor.prop

The .aggressor.prop file is the Cobalt Strike config file for the GUI. It can be found in the user's home directory.

Scripts added via the GUI will be added to this file. You can also edit the file directly before starting the CS GUI. This can be used to deploy a common set of scripts.

The option `cortana.scripts` contains the a `\!\!` separated list of full paths

Example of loading two scripts

```perl
cortana.scripts=/home/user/Development/aggressor_script_notes/misc_functions.cna\!\!/home/user/Development/aggressor_script_notes/data_models.cna
```

## Contribute

If you'd like to contribute..

- Submit a [pull request](https://github.com/Cobalt-Strike/aggressor_script_examples/pulls)
- Do no include complex scripts with multiple components. The intent is to provide quick references
- Update the index
- Keep content organized

## References

- [Community Kit](https://cobalt-strike.github.io/community_kit)
- [Aggressor Scripting](https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics_aggressor-scripts/agressor_script.htm)
- [Sleep Manual](http://sleep.dashnine.org/manual/)
