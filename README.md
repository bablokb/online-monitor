Simple Online-Monitor
=====================

This is a simple online-monitor script, started by a systemd service.
It logs the online-status to the file `/var/log/online-monitor.log`. It
tries to ping an ip-address and if that fails the script diagnoses the
"offline"-state.


Installation
------------

Download the software and run install:

    git clone https://github.com/bablokb/online-monitor
    cd online-monitor
    sudo tools/install

At system startup the systemd-service `online-monitor.service` will
start the script automatically. If you prefer a manual start, run

    sudo systemctl disable online-monitor.service
    sudo systemctl start   online-monitor.service

The first command is only necessary once.


Configuration
-------------

Please edit the script `/usr/local/sbin/online-monitor` directly. You
can change the ip-address and the ping interval.

If you want to run some own code depending on the online-status, you
have to edit the functions `on_online()` or `on_offline()`. The latter
contains some example code, e.g. to bring an interface up again.

If unit-file of the systemd-service is
`/etc/systemd/system/online-monitor.service`. Usually, there is no need
to edit this file.
