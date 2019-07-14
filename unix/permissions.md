# Unix File/Directory Permissions

## File:
- **setuid for execution** *(4000)* - file executed by any user will get execution privileges of **user** who owns the file.
- **setgid for execution** *(2000)* - file executed by any user will get execution privileges of **group** who owns the file.
- **sticky** *(1000)* - *not used with files*

## Directory:
- **setuid for new files/dirs (4000)** - *not used with directories*
- **setgid for new files/dirs (2000)** - every file or directory created in this directory inherits **group** of this directory instead of getting owners group as usual
- **sticky/restricted deletion flag (1000)** - only file/directory owner can rename, move or delete even if this directory has write access for all

## Where special bits are encoded

- **setuid** (4000) shown on owning USER,
- **setgid** (2000) shown on owning GROUP,
- **restricted deletion flag (sticky)** (1000) set on others


### How to read special bits

- **s**: setuid/setgid (**also executable**)
- **t**: sticky (**also executable**)
- **S**: setuid/setgid (**not executable**)
- **T**: sticky (**not executable**)
- **x**: **executable** only - without any special bits

**-rwsr-Sr-t**: a file whose user class has read, write and execute permissions; whose group class has read permission; whose others class has read and execute permissions; and which has setuid, setgid and sticky attributes set.

### Example permissions

	---S--S---	6000	setuid, setgid
	d-----S--T	5000	setgid, restricted deletion
	---s--s--x	6111	setuid, setgid
	d--x--s--t	5111	setgid, restricted deletion
	----------	0000	no permissions
	-rwx------	0700	read, write, & execute only for owner
	-rwxrwx---	0770	read, write, & execute for owner and group
	-rwxrwxrwx	0777	read, write, & execute for owner, group and others
	---x--x--x	0111	execute
	--w--w--w-	0222	write
	--wx-wx-wx	0333	write & execute
	-r--r--r--	0444	read
	-r-xr-xr-x	0555	read & execute
	-rw-rw-rw-	0666	read & write
	-rwxr-----	0740	owner can read, write, & execute; group can only read; others have no permissions

> * 4 - read
> * 2 - write
> * 1 - execute
