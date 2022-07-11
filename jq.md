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
## Count Items in Dictionary
```
{
  "KEY1": {
    "TABLE1": {},
    "TABLE2": {},
    "TABLE3": {}
  },
  "KEY2": {
    "TABLE4": {}
  },
  "KEY3": {
    "TABLE5": {},
    "TABLE6": {}
  }
}
```
First, count values in each key:
```
jq '.[] | length' file.json
3
1
2
```
Turn results into an array:
```
jq '[.[] | length]' file.json
[
  3,
  1,
  2
]
```
Sum the array:
```
jq '[.[] | length] | add' file.json
6
```
## Extract Objects Recursively
```
jq '[recurse(.children[]) | del(.children)]' file.json
```
