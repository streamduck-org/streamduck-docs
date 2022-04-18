# Getting started
This is required only if you used manual methods, if you installed Streamduck with an installer, it should have already done this

### 1. Dedicate a folder for daemon
Create a folder somewhere where Streamduck will be keeping device configs and everything related.

### 2. Run Daemon in the folder
Navigate to the folder with cmd/terminal and run `streamduck_daemon`

This will start the daemon, and it should already be usable at this point.

### (Optional) 3. Autostart the daemon

#### Windows

Currently, there's no installer for Windows which would had added autostart. So you have to make a bat file that runs streamduck_daemon in specific folder, and add it to Startup folder

Example of the file:
```
cd C:\streamduck_daemon_folder
streamduck_daemon
```

And it should be placed to `%appdata%\Microsoft\Windows\Start Menu\Programs\Startup`


#### Linux
This can be either done by having your Desktop Environment run the daemon on start, or using a user systemd service.

Systemd service example:
```
[Unit]
Description=Streamduck Daemon

[Service]
WorkingDirectory=PATH_TO_STREAMDUCK_FOLDER
ExecStart=PATH_TO_STREAMDUCK_DAEMON_EXECUTABLE
(if installed with cargo, should be /home/<user>/.cargo/bin/streamduck_daemon)

[Install]
WantedBy=multi-user.target
```
The service should be installed in `~/.config/systemd/user/`

Following commands can be used to add the daemon to autostart and run it:
```
systemctl --user enable streamduck-daemon.service
systemctl --user start streamduck-daemon.service
```