# Using pre-packaged binaries
Binaries are available for Windows and Linux users on [the release page](https://github.com/streamduck-org/streamduck-gui/releases) of Streamduck GUI project

## Windows
Windows users get a setup executable, running the setup will automatically install the GUI and open it after

Shortcut will be added to start menu and the GUI can be launched from that

## Linux
Linux users get a self-contained AppImage which can be executed to bring up the GUI client, as simple as that

If you prefer, it can also be placed into `.local/bin` if you want to be able to launch if from terminal, or you can create a desktop file for it for more convenient way of launching the GUI

# Building from source
The GUI can be also built from source. The GUI runs on NodeJS v16, make sure you use that version, other versions might not work.

1. Clone the repo using following command
```shell
git clone https://github.com/streamduck-org/streamduck-gui.git
```

2. Install dependencies using following command
```shell
npm install
```

3. Build or serve the GUI, depending on if you just want to run the GUI, or get a package
```shell
npm run electron:serve
```
or
```shell
npm run electron:build
```