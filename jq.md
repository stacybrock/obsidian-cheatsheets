# jq
## Get keys
Root-level keys:
```
jq keys[] file.json
```
Keys for deeper node:
```
jq .somekey | keys[] file.json
```
## Extract Objects Recursively
```
jq [recurse(.children[]) | del(.children)] file.json
```
