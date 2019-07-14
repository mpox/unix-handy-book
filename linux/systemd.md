# systemd

**List** of all available services and their status

    systemctl

Stats and **tree** of running processes

    systemctl status

**Poweroff** system

    systemctl poweroff

**Status** of a particular service unit

    systemctl status <unit>

Enable particular service unit to be run on **system startup**

    systemctl enable <unit>

Disable particular service unit from being run on system startup

    systemctl disable <unit>

Start particular service unit

    systemctl start <unit>

Stop particular service unit

    systemctl stop <unit>

Show all system logs since boot

    journalctl -b

Show current system logs and follow (keep displaying new logs)

    journalctl -f

Show logs of particular service unit

    journalctl -u <unit>

Show logs of a particular service unit since system boot, do not divide logs in to pages

    journalctl --no-pager -b -u <unit>

Set maximum size of all logs

    journalctl --vacuum-size=100M

Run application as a given user

    runuser -u ctrld venv/bin/python pm-connect.py

Run application as a given user and group

    runuser -u ctrld -g ctrld -- sudo /sbin/systemctl poweroff -i
