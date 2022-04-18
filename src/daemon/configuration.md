# Configuration
Daemon configuration file tells the daemon what folder locations to use, pooling rate and socket settings

File `config.toml` should be located in daemon's working folder, if it doesn't exist, create one if you want to change anything

Streamduck uses default values for config values if they don't exist, so you don't have to add everything if you just want to change pooling rate. Default values are used in examples

Here's what you can change using the config file:

#### Pooling rate
This determines frequency of how often Streamduck will try to get button states from Stream Deck. Frame rate of animated images will also depend on this. Decreasing this might use less CPU, sacrificing responsiveness and frame rate of animated images 

The parameter accepts positive integer. The larger the number, the more frequent pooling will be done
```toml
pool_rate = 150
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