# Pacman - package manager

Search for regexp "ne.hack" in package database.

```
pacman -Ss ne.hack
```

Download and install gpm including dependencies.

```
pacman -S gpm
```

Install ceofhack-0.6-1 package from a local file.

```
pacman -U /home/user/ceofhack-0.6-1-x86_64.pkg.tar.gz
```

Synchronize db

```
pacman -Syy
```

Show package info

```
pacman -Qi <package>
```

List all installed files by a package

```
pacman -Qlq <package>
```

Remove package

```
pacman -R package_name
```

Download only

```
pacman -Sw
```

List all packages from given repository

```
pacman -Sl <repo>
```

Finds full package path from a given repository

```
pacman -Sp --noconfirm
```

Lists packages' names from given package db

```
cat /var/lib/pacman/sync/core.db | tar -tvz | grep -e "^d" | awk '{print $6}'
```

List of packages to be updated

```
pacman -Sup --noconfirm
```

Updates all packages

```
pacman -Syu
```
