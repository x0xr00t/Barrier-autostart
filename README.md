# Barrier-autostart
/etc/systemd/system/barrier.service files for auto boot barrier on start up 


# make config file in /etc/systemd/system
* nano barrier.service

# Add these lines
[Unit]
Description=Barrier mouse/keyboard share
Requires=display-manager.service
After=display-manager.service
StartLimitIntervalSec=0

[Service]
Type=simple
ExecStart=/bin/bash -c 'exec /usr/bin/barrierc -f --enable-crypto {Ip-Barrier-Server} </dev/zero' 
Restart=always
RestartSec=1
User={YOUR SYSTEM USER}

[Install]
WantedBy=multi-user.target


# Test service 
* systemctl restart barrier

# Enable System Service at bootup 
*systemctl enable barrier
Created symlink /etc/systemd/system/multi-user.target.wants/barrier.service ? /etc/systemd/system/barrier.service.


:D Cheers 
