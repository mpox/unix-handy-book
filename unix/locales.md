# Locales


	export LC_ALL=C.UTF-8

	localedef -v -c -i en_US -f UTF-8 en_US.UTF-8


### Method 1 - mac:

Terminal > Preferences > Select Terminal type such as Basic (default) > Advanced tab
Make sure that the ‘Set locale environment variables on startup’ is unchecked as follows:

### Method #2: Preventing OpenSSH Client from sending the LC_* variables on OS X / Linux / Unix desktop

Edit /etc/ssh/ssh_config or /etc/ssh_config file, enter:
$ sudo vi ~/.ssh/config
Remove or comment out as follows:

	SendEnv LANG LC_*

### Option #3: Install required locale on the remote server

On remote system

	localedef -i en_US -f UTF-8 en_US.UTF-8


source: https://websetnet.net/os-x-terminal-bash-warning-setlocale-lc_ctype-cannot-change-locale-utf-8-no-such-file-or-directory-fix-2/
