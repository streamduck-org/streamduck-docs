# Using Installers
There's an installer currently for Windows only, you can get it from the [Releases page](https://github.com/streamduck-org/streamduck/releases)

The installer installs the daemon with all the necessary configuration to it, and additionally a CLI client too

After installation, you can check [daemon configuration page](daemon/configuration.md) in case you want to change any of the settings of the daemon, you can check [CLI usage page](cli/usage.md) to learn more about the CLI client. 

You should check out [GUI installation page](gui/install.md), if you want a graphical interface. Recommended for Windows users 

The daemon is usually installed into Program Files on Windows in a folder called Streamduck

Linux setup script will be eventually available, for now Linux users have to use the [cargo way](#using-cargo)

# Using Cargo

Streamduck is published on [crates.io](https://crates.io/search?q=streamduck), Rust language's package repository.

### Make sure you have Rust toolchain installed

If you don't have it installed, install it from here: [rustup.rs](https://rustup.rs/) <br> 
The project is using 1.59 version of Rust compiler.

### Dependencies
Compilation of the project requires libusb and on Linux - libxdo. You can install the dependencies using following command on Ubuntu:
```shell
sudo apt update
sudo apt-get install libusb-1.0-0-dev libxdo-dev
```
Arch: 
```shell
pacman -S libusb xdotool
```

On Windows it should pull the dependencies automatically if Windows updates don't break anything

### Cargo
Once you have up to date version of Rust toolchain, use following command to install Streamduck daemon from crates.io:
```
cargo install streamduck-daemon
```
Git repository will usually have the latest code, but not always the most stable. If you want to install from git repository:
```
cargo install --git https://github.com/streamduck-org/streamduck.git streamduck-daemon
```
<br>

# Udev rules
This is required only for linux users. 

It's required to add udev rules to be able to connect to HID devices without having root access.

To install udev rules for Stream Deck devices, use following commands:
```
wget https://raw.githubusercontent.com/streamduck-org/streamduck/master/sh/40-streamdeck.rules
sudo mv 40-streamdeck.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger
```