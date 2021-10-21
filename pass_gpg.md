# Pass For GPG Cheatsheet
## GPG Pre-requisites
Get the ID of the signing key. (Don't have one? See [[gpg|GPG]])

**List GPG keys:**
```
$ gpg --list-keys
/Users/brock/.gnupg/pubring.kbx
------------------------
pub   rsa4096 2019-07-19 [SC]
      X55XXX5555X5X555X5X5XX555XX5E55555555555
uid           [ultimate] Stacy Brock <nope@redacted.edu>
sub   rsa4096 2019-07-19 [E]
```

`X55XXX5555X5X555X5X5XX555XX5E55555555555` is the ID of the public key.

## Pass

**Initialize Pass**
```
$ pass init "X55XXX5555X5X555X5X5XX555XX5E55555555555"
```

**Add New Entry**
```
$ pass insert Folder/EntryName
```

**Delete Entry**
```
$ pass delete Folder/EntryName
```

**Show An Entry**
```
$ pass Folder/EntryName
supersekretstuff
```

**List All Entries**
```
$ pass
Password Store
└── Folder
    └── EntryName
```
## Troubleshooting
### gpg: WARNING: server 'gpg-agent' is older than us
Occurs after GnuPG has been updated. Solution is to kick `gpg-agent`
```shell
$ gpgconf --kill -v gpg-agent
```
