# Using Cargo

Streamduck is published on [crates.io](https://crates.io/search?q=streamduck), Rust language's package repository.

### Make sure you have Rust toolchain installed

If you don't have it installed, install it from here: [rustup.rs](https://rustup.rs/) <br> 
The project is using 1.59 version of Rust compiler.

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