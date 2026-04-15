## 11. Adding a swap file in Linux Mint

This system originally had no active swap space, so I created and enabled a 16 GiB swap file.

### Commands used

Create the swap file:
```bash
sudo fallocate -l 16G /swapfile
```
This command creates a 16 GiB file called /
`swapfile`, which will later be used as swap space.

Set secure permissions:
```bash
sudo chmod 600 /swapfile
```
This command sets strict permissions so only the 
root user can read and write the swap file.
Example: `6 = read + write for owner`, `0 = no 
permissions for group`, `0 = no permissions for others`.

Prepare the file as swap:
```bash
sudo mkswap /swapfile
```
This command formats the file so Linux can recognize
and use it as swap space.
```bash
sudo swapon /swapfile
```
This command activates the swap file immediately, so 
the system can start using it without a reboot.

Make it persistent after reboot:
```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```
This command adds the swap file entry to `/etc/fstab`,
so the system enables it automatically after every reboot.

Check active swap:
```bash
swapon --show
```
This command shows whether the swap file is currently active.

Check memory and swap usage:
```bash
free -h
```
This command displays RAM and swap usage in a human-readable format.

Check system summary:
```bash
inxi -F
```
This command provides a general system overview, including swap
detection and basic hardware information. Use `sudo inxi -F` if
you want more detailed information.

### Result
The system now correctly recognizes and uses an active 16 GiB swap file located at /`swapfile.`
