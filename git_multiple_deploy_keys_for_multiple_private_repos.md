# Multiple Deploy Keys For Multiple Private Git Repos

Given two private [[git]] repos named `repo1` and `repo2`...

1. Generate keypairs for each repo:

- `repo1`: `repo1.github.id_rsa` and `repo1.github.id_rsa.pub`
- `repo2`: `repo2.github.id_rsa` and `repo2.github.id_rsa.pub`

2. Add the keys to their respective repos as Deploy Keys.

3. Edit `.git/config` in each repo to point to a "fake" unique subdomain at GitHub (.com or a local Enterprise):

    In `repo1/.git/config`...
	```
	[remote "origin"]
        url = "ssh://git@repo1.github.com/org/repo1.git"
	```

	In `repo2/.git/config`...
	```
	[remote "origin"]
			url = "ssh://git@repo2.github.com/org/repo2.git"
	```

4. Edit SSH config to use the correct ssh for each subdomain.

	In `$HOME/.ssh/config`...
	```
	Host repo1.github.com
	  HostName repo1.github.com
	  User git
	  IdentityFile ~/.ssh/repo1.github.id_rsa
	  IdentitiesOnly yes

	Host repo2.github.com
	  HostName repo2.github.com
	  User git
	  IdentityFile ~/.ssh/repo2.github.id_rsa
	  IdentitiesOnly yes
	```
