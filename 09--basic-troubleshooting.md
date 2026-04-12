# 09 - Basic Troubleshooting

## Purpose
This file contains basic notes about a simple troubleshooting approach in Linux and IT support work.

## Basic idea
Troubleshooting means finding the cause of a problem step by step instead of guessing.

## Simple troubleshooting process

### 1. Identify the problem
Understand what is not working.

Examples:
- internet does not work
- a service does not start
- a command returns an error
- a file cannot be found

### 2. Check the obvious first
Start with the simplest possible checks.

Examples:
- is the cable connected
- is the network interface up
- is the service running
- is the file path correct
- was the command typed correctly

### 3. Read the error message
Error messages often give direct clues.

Example:
command not found

This may mean:
- the command is not installed
- the command name is wrong
- the command is not in PATH

### 4. Check logs
Logs often explain what happened.

Examples:
- `/var/log/syslog`
- `/var/log/auth.log`
- `journalctl`

### 5. Test one thing at a time
Do not change many things at once.

This makes it easier to see what caused the result.

### 6. Confirm the fix
After making a change, test again and confirm the issue is solved.

## Useful examples

### Check if a service is running
Example:
systemctl status ssh

### Check running processes
Example:
ps aux

### Test network connectivity
Example:
ping 8.8.8.8

### View system logs
Example:
journalctl

## Note
A good troubleshooter stays calm, checks basic things first, reads errors carefully, and works step by step.
