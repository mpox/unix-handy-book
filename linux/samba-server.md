# Samba - Server

### Setup

You need to install and run `smbd`

### Manage Samba users

To allow clients to access shares as an authorized users, the user have to be created on server. To create Samba user a unix user must already exist in the system (in /etc/passwd)

	smbpasswd -a <username>


Delete/Disable/Enable Samba user

	smbpasswd -x <username>
	smbpasswd -d <username>
	smbpasswd -e <username>

**NOTE:** Users can be added only when `smbd` is running

List all users

	pdbedit -L -v

### Example Samba Config file

```
[global]
server string = Polo Magellan
workgroup = WORKGROUP
security = user
encrypt passwords = yes
wins support = yes
local master = no
preferred master = no
os level = 30
short preserve case = yes
preserve case = yes
guest account = music
unix password sync = no

map to guest = Never

[Internal Storage]
        comment = Polo Magellan Internal Storage
        path = /media/INTERNAL
        read only = no
        guest ok = no
        create mask = 0744
        directory mask = 0755
        follow symlinks = no
        force group = ftp

[NAS]
        comment = Polo Magellan Connected NAS Drives
        path = /media/NAS
        read only = no
        guest ok = no
        create mask = 0744
        directory mask = 0755
        follow symlinks = no
        force group = ftp

```

### Enable Guest Access
To enable Guest access, do few changes in config:

- `map to guest` to `Bad User` and
- `guest ok` to `yes`
