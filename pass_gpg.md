# Pass and GPG

## GPG Key

**Generate a new GPG key:**
```
$ gpg --full-generate-key
```

**List GPG keys:**
```
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
