# Wi-Fi Troubleshooting: Hotspot Packet Loss on Linux Mint

## Problem
While using a Samsung Galaxy S25 Ultra mobile hotspot on Linux Mint, the Wi-Fi connection felt unstable even though the signal strength looked very good.

## Environment
- Laptop: ASUS G551JK
- OS: Linux Mint 22.3
- Wi-Fi interface: `wlp4s0`
- Hotspot source: Samsung Galaxy S25 Ultra

## Initial symptoms
- Strong signal in `iwconfig`
- Unstable internet experience
- Packet loss
- Latency spikes
- High transmission retries
- Connection initially using `2.4 GHz`

## Commands used

### Check wireless status
```bash
iwconfig
```
Test internet latency

```bash
ping -c 20 1.1.1.1
```

Find default gateway

```bash
ip route
```

Test local connection to hotspot

```bash
ping -c 20 <gateway_ip>
```

## Findings
The main issue was not weak signal strength.

The issue was the local wireless link between:
- laptop ↔ phone hotspot

Important clues:
- strong signal
- poor bit rate on 2.4 GHz
- high transmission retries
- packet loss to the local gateway

## Temporary fix
Disable Wi-Fi power saving:

```bash
sudo iwconfig wlp4s0 power off
```

## Permanent fix
Create this file:

```bash
sudo nano /etc/NetworkManager/conf.d/wifi-powersave-off.conf
```

Add:

```ini
[connection]
wifi.powersave = 2
```
Then restart NetwokManager:

```bash
sudo systemctl restart NetworkManager
```

## Intermediate result
Disabling Wi-Fi power saving improved performance immediately.

The reported bit rate increased from roughly `~50 Mb/s` to `144 Mb/s`, and the connection felt much faster.

However, intermittent instability still remained, so the issue was only partially resolved at this stage.

This suggested that Wi-Fi power saving was one cause, but the hotspot band (`2.4 GHz`) was still another important bottleneck.

## Additional improvement
Change the phone hotspot band from:
- `2.4 GHz`

to:
- `5 GHz`

## Final result
After:
- disabling Wi-Fi power saving
- switching hotspot to `5 GHz`

the connection became significantly more stable.

Confirmed improvements:
- `Power Management:off`
- bit rate increased further
- transmission retries dropped to `0`
- packet loss to the gateway dropped to `0%`

## Key lesson
A strong Wi-Fi signal does not always mean a healthy Wi-Fi connection.

A better troubleshooting flow was:
1. check interface status with `iwconfig`
2. test internet latency
3. find the real gateway with `ip route`
4. test packet loss to the local gateway
5. test Wi-Fi power saving
6. test hotspot band (`2.4 GHz` vs `5 GHz`)

## Useful commands summary
```bash
iwconfig
ip route
ping -c 20 1.1.1.1
ping -c 20 <gateway_ip>
sudo iwconfig wlp4s0 power off
sudo systemctl restart NetworkManager

