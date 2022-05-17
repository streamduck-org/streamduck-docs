# Explanation of Core Design
A bit of explanation needed to make sure you understand how Streamduck works, it's different from the official software

## Components instead of button types
Instead of having only one thing a button can do, Streamduck's buttons are containers of components. Many components can be put on a button, which makes a single button perform a bunch of different actions at once

Components are unique however and there cannot be multiple of same components on a single button. The component should itself support multi-action if it needs to, implementations of multi-actions similar to official software will arrive later

## Plugins are everything
This software was designed with extensibility as main goal, the software has only essential functionality out of the box. Everything else that you might want will be added by plugins

This allows the project to thrive even when the core stops being actively developed. Plugins can really do a lot of things with this software

## Images are part of device configuration
Images are kept inside of device configs as collection of identifiers to binary data

This allows device configs to be self-contained and not rely on any external files, this also enables images to be uploaded over network using WebSocket 

## Clients are only messengers
Everything you do with Streamduck is managed by the daemon, clients only tell daemon what to do

So even if you decide to copy a button and close the client, the clipboard for buttons is kept on the daemon side. No progress will be lost, and you can even open a different client and paste from there, and you'll observe the button you copied from different client

Due to focus of separately having a daemon, clients are considered separate projects. The main project is the core and daemon

## Devices are not automatically managed
Unlike official software, Streamduck will not automatically manage all found Stream Deck devices, you need to tell the daemon to manage the device 

This was made with assumption that someone might be using Stream Deck for some other purpose, and to avoid conflicts, the user should tell the daemon to manage the device, and not the daemon deciding to automatically take the device

## Conclusion
Some more information will be explained in documentation of the clients, proceed to [CLI](../cli/install.md) or [GUI]() section