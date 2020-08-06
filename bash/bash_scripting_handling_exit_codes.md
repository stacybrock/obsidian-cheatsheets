# Bash Scripting: Handling Exit Codes
Example of how to handle exit codes in a [[bash]] script...

```bash
#!/bin/bash

touch /root/test 2> /dev/null

if [ $? -eq 0 ]
then
  echo "Successfully created file"
  exit 0
else
  echo "Could not create file" >&2
  exit 1
fi
```

Source: http://bencane.com/2014/09/02/understanding-exit-codes-and-how-to-use-them-in-bash-scripts/
