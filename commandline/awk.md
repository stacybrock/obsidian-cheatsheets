# awk Cheatsheet

## One Liners

**Tabularize CSV**
```
$ cat iam-infra-ghe.csv | awk '{gsub(/,/, ""); printf "%-15s %-13s %s\n", $1, $2, $3}'
```

## Change Field Separator

```
$ awk 'BEGIN { FS = "," }; {print $2}' somefile.csv
$ awk -F',' '{print $2}' somefile.csv
```

## Strip Quotes (or Other Things) from a Field

**Strip Double-Quotes**
```
$ awk '{gsub(/"/, "", $2); print $2}' somefile.csv
```

**Strip Single-Quotes**
```
$ awk '{gsub(/'\''/, "", $1); print $1}' somefile.txt
```
`'\''` is essentially a 4-character escape sequence for a `'` (single quote)

## Quick IP Address
```
$ curl ipinfo.io
```
