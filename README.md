# Arch Linux Eduroam Wi-Fi Stability Fix (NetworkManager)

This repo documents a small NetworkManager configuration change that fixed repeated
disconnect/reconnect loops on **Eduroam** (802.1X) on **Arch Linux** in my setup.

## Symptoms
- Random Eduroam disconnects
- Continuous connect/disconnect loop
- Connection works briefly, then drops

## What helped in my case
### 1) Disable scan-time MAC randomization
Some Eduroam deployments are sensitive to MAC randomization and may become unstable.

File:
`/etc/NetworkManager/conf.d/disable-wifi-sleep.conf`

```ini
[device]
wifi.scan-rand-mac-address=0

[connection]
autoconnect-retries=0
```

### 2)Disable Wi-Fi power saving
Wi-Fi power saving can cause connection instability on some hardware and drivers, 
especially with enterprise networks like Eduroam.

File:
`/etc/NetworkManager/conf.d/00-wifi-powersave.conf`

```ini
[connection]
wifi.powersave=2
```
