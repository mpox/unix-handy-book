# Unix User Accounts

Add user account with home directory (`-m` parameter)

	useradd -m <user name>

> User created this way is inactive (cannot sign in). You can use `-p` parameter to give an encrypted password, as returned by `crypt` command


Set password for created user

	passwd <user name>


Add user to a group

    usermod -a -G svn user

    usermod -a -G examplegroup exampleusername
