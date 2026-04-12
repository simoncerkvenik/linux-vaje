# 06 - System and Processes

## Purpose
This file contains basic notes about processes, services, and service management in Linux.

## Common commands

### `ps aux`
Shows running processes.

Example:
ps aux

### `systemctl status`
Shows the status of a service.

Example:
systemctl status ssh

### `systemctl start`
Starts a service.

Example:
sudo systemctl start ssh

### `systemctl stop`
Stops a service.

Example:
sudo systemctl stop ssh

### `systemctl enable`
Enables a service to start at boot.

Example:
sudo systemctl enable ssh

### `systemctl disable`
Disables a service from starting at boot.

Example:
sudo systemctl disable ssh
