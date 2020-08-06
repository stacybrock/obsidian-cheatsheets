# Bash Scripting: Exit Traps

Ensure a [[bash]] script always performs necessary cleanup operations, even when something unexpected goes wrong.

```bash
#!/bin/bash

scratch=$(mktemp -d -t tmp.XXXXXXXXXX)

function finish {
  rm -rf "$scratch"
}
trap finish EXIT

## DO WORK HERE
```

**IMPORTANT:** Placement of the finish/trap matters!

Source: http://redsymbol.net/articles/bash-exit-traps/
