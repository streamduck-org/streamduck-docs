# Configuration
This page explains a bunch of different things that can be configured about Streamduck daemon

Configuration folder:

- Linux: `$XDG_CONFIG_HOME/streamduck` or `$HOME/.config/streamduck`
- MacOS: `$HOME/Library/Application Support/streamduck`
- Windows: `{FOLDERID_RoamingAppData}/streamduck` (` %APPDATA%/streamduck`)

**This folder has to be manually created.**

> If your system is not supported it will use the current working directory

## Configuration file

File `config.toml` should be located in your configuration folder, if it doesn't exist, create one if you want to change anything.

> You can use a different location with the `--config-path` option

Streamduck uses default values for config values if they don't exist, so you don't have to add everything if you just want to change pooling rate. Default values are used in examples

Here's what you can change using the config file:

#### Frame rate
This determines frame rate of animated images

The parameter accepts positive integer. The larger the number, the more FPS you'll be able to get
```toml
frame_rate = 100
```

#### Reconnect rate
This determines how often Streamduck will be checking for disconnected devices

The parameter accepts seconds in positive float format
```toml
reconnect_rate = 1.0
```

#### Device config path
This tells Streamduck where to keep device configs, folder will be created if it doesn't exist 
```toml
device_config_path = "./devices"
```

#### Plugins path
This tells Streamduck where it should seek for plugins. If there's no folder at path, nothing will be loaded
```toml
plugin_path = "./plugins"
```

#### Plugin settings path
This tells Streamduck at what path it should create json file for keeping settings of plugins
```toml
plugin_settings_path = "./global.json"
```

## Custom fonts
Custom fonts can be installed by creating a folder called `fonts` in your configuration folder, and dropping in .ttf or .otf files.

Fonts will be automatically loaded on next run of the daemon, and will be available to be selected in Streamduck clients.

## Plugins
Plugins can be installed by dropping dynamic library files (.dll or .so for respective platform) into `plugins` folder inside your configuration folder.

Plugins will be automatically loaded on next run of the daemon. If any error happens during plugin loading, it will be logged by the daemon. So if something doesn't work, check logs of the daemon and find out 
