# Usage
This page explains how to get started with Streamduck through a CLI client

## Add your device
Before you can do anything, you need to tell daemon to manage your device

Run the CLI in your terminal/CMD

```shell
streamduck-cli
```

List devices found on your computer
```shell
device list
```
If you don't see any devices, make sure your Stream Deck is connected. If you're on Linux, make sure you've installed Udev rules as explained in [this section](../install.md#udev-rules)

Add your device using serial number
```shell
device add <serial number>
```

## Select your device
CLI requires a device to be selected before any of device commands can be executed, you can do this by using this command:
```shell
select <serial number>
```

## Configure your layout
You can now configure layout of your buttons and components however you want. You can find all the commands explained [here](commands.md)

## Make sure you save
Your layout will persist until the daemon gets shut down, if you want to save it, so it will remain longer than that, use following command:
```shell
config save
```
It will save config of currently selected device, if you want to save all devices:
```shell
config save all
```