# APT

### Which installed software packages use the most disk space on Debian?

The easiest way (without installing extra packages) is:

    dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
which displays packages in size order, largest package last.

Unfortunately on at least some systems, this list includes packages that have been removed but not purged. All such packages can be purged by running:

    dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
Or if you don't want to purge uninstalled packages you can use this variant to filter out the packages which aren't in the 'installed' state from the list:

    dpkg-query -Wf '${db:Status-Status} ${Installed-Size}\t${Package}\n' | sed -ne 's/^installed //p'|sort -n

List installed packages sorting by size on disk

	aptitude search "~i" --display-format "%I %p" --sort installsize


source: https://unix.stackexchange.com/questions/40442/which-installed-software-packages-use-the-most-disk-space-on-debian
