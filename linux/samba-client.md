# Samba - Client

### Samba shares

List all Samba shares in current neighbourhood:

	smbtree -N

Example Result

	WORKGROUP
	    \\SZAFA                     SZAFA
	        \\SZAFA\LIBRARY         SSDPR-CX 400-128's LIBRARY
	        \\SZAFA\NONVOLATILE     SSDPR-CX 400-128's NONVOLATILE
	        \\SZAFA\ipc$            IPC Service (SZAFA)
	    \\SILVERADO                 Silverado

### Samba mount

Podłączanie zasobu \\\\SZAFA\\LIBRARY

	mount -t cifs -o user=music,password=polomagellan \\\\SZAFA\\LIBRARY /mnt/1

lub

	mount -t cifs -o user=music,password=polomagellan //SZAFA/LIBRARY /mnt/1

> Uwaga, jeżeli hasło bedzie miało przecinek to nie zadziała. Można użyć wówczas innej metody przekazywania hasła - albo przez zmienną środowiskową PASSWD, albo przez plik credentialsów

	mount -t cifs -o cred=<filename> //SZAFA/LIBRARY /mnt/1

Plik z poświadczeniami - ``<filename>``

	username=value
	password=value
	domain=value

Montowanie zasobu jako gość

	mount -t cifs -o guest "//SZAFA/LIBRARY/" /mnt

Niektóre serwery obsługują tylko protokół w starej wersji

	mount -t cifs -o guest,vers=1.0 "//SZAFA/LIBRARY/" /mnt

### Wersje protokołu

SMB protocol version. Allowed values are:

- 1.0 - The classic CIFS/SMBv1 protocol.

- 2.0 - The SMBv2.002 protocol. This was initially introduced in Windows Vista Service Pack 1, and Windows Server 2008. Note that the initial release  version  of  Windows  Vista  spoke  a
  slightly different dialect (2.000) that is not supported.

- 2.1 - The SMBv2.1 protocol that was introduced in Microsoft Windows 7 and Windows Server 2008R2.

- 3.0 - The SMBv3.0 protocol that was introduced in Microsoft Windows 8 and Windows Server 2012.

- 3.1.1 or 3.11 - The SMBv3.1.1 protocol that was introduced in Microsoft Windows Server 2016.

Note too that while this option governs the protocol version used, not all features of each version are available.

The  default  since v4.13.5 is for the client and server to negotiate the highest possible version greater than or equal to 2.1. In kernels prior to v4.13, the default was 1.0. For kernels
between v4.13 and v4.13.5 the default is 3.0.


### Samba servers

Following command is a very little known secret of Samba. It returns IP adresses of all Samba servers in one's own broadcast domain:

	nmblookup __SAMBA__

This one returns a list of all NetBIOS names and their aliases of all Samba servers in the neighbourhood (it does a 'node status query'):

	nmblookup -S __SAMBA__

This one returns a list of all IP adresses of SMB servers (that is, Linux+Unix/Samba or Windows) in the neighbourhood:

	nmblookup '*'

Finally, all NetBIOS names and their aliases of all SMB servers (Linux+Unix/Samba or Windows):

	nmblookup -S '*'
