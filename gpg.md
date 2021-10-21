# GPG Cheatsheet
#### Generate a new GPG Key
```
$ gpg --full-generate-key
```
RSA 4096

#### List GPG Keys
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

#### Generate Revocation Certificate
```
$ gpg --output ~/revocation.crt --gen-revoke your_email@address.com
```
It's generally a good idea to generate revocation certificates as soon as a new signing key is created. Generate one revocation certificate for each possible reason, as the reason will be baked-in to the resulting file and can't be changed when you need it.
1. compromised
2. superceded
3. unused

Store the revocation certificate files in a secure location separate from the signing key.