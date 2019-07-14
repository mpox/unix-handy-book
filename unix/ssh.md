# SSH keys

Generate default key pair for the current user

	ssh-keygen -t rsa

Generate 2048-bit key for given e-mail address and store it to given file

	ssh-keygen -t rsa -b 2048 -C "your_email@example.com" -f ~/.ssh/id_rsa

Add key to trusted at target host

	ssh-copy-id -i ~/.ssh/id_rsa.pub gitadmin@polomagellan.pl

Add key to trusted at target host with custom port

	ssh-copy-id -i ~/.ssh/id_rsa.pub "gitadmin@polomagellan.pl -p1234"

Add key to trusted at target host - manual method

	cat ~/.ssh/id_rsa.pub | ssh gitadmin@polomagellan.pl "mkdir -p .ssh && cat >>  ~/.ssh/authorized_keys"

> If target host still asks for password, please make sure
a target host's home directory has permission restricted to 755

Remove fingerprint of target host from trusted

	ssh-keygen -R 10.8.8.220

> Very useful when host has changed it's key and it needs 
to be refreshed

Remove host from trusted at line #6

sed -i ‘6d’ ~/.ssh/known_hosts

> It might not work on MacOS

Remove host from trusted at line #6 (Perl method)

	perl -pi -e 's/\Q$_// if ($. == 6);' ~/.ssh/known_hosts

