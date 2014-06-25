# bash options-parse

Nicely formatted usage messages and arguments parsing for bash scripts.

There are probably thousands of scripts like this one. I've made it as an exercise to learn a little more bash, any feedback appreciated!

Version: 0.1

## Example

```bash
#!/bin/bash

   OP_NAME="Example"
  OP_USAGE="example [options]"
OP_VERSION="1.0.0"

OP_OPTIONS=(
	# -SHORT_NAME[:ARGUMENT_NAME] (-|--LONG_NAME) DEFAULT_VALUE DESCRIPTION

	-v:level --verbose 2     "Level of verbosity, from 0 (quiet) to 10 (drunk uncle)."
	-f       --flag    false "A flag... Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
	-p:port  -         54321 "One with no long name"
)
. options-parse

# To access an option value, use ${ARGS[op_SHORT_OR_LONG_NAME]}:
echo "Verbosity: ${ARGS[op_verbose]} or ${ARGS[op_v]}"
echo "     Flag: ${ARGS[op_flag]} or ${ARGS[op_f]}"
echo "     Port: ${ARGS[op_p]}"
```

It also provide a nicely formatted `--help`:

	$ example --help
	
	Example

	USAGE: example [options]

	VERSION: 1.0.0

	OPTIONS:

	 -v, --verbose <level> [2]
	    Level of verbosity, from 0 (quiet) to 10 (drunk uncle).

	 -f, --flag [false]
	    A flag... Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim 
	    ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in 
	    voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt 
	    mollit anim id est laborum.

	 -p <port> [54321]
	    One with no long name
