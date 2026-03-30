# Arch Linux Eduroam Wi-Fi Stability Fix (NetworkManager)

This repo documents a small NetworkManager configuration change that improved Wi-Fi stability on Arch Linux in my setup, especially for Eduroam and resume-from-suspend issues.

## What this fixes

In my case, the main problems were:

- random Wi-Fi disconnects
- unstable reconnect behavior after suspend / opening the laptop lid
- NetworkManager not recovering cleanly after a drop
- general instability on Eduroam with NetworkManager defaults

## What helped in my case

I made a single Wi-Fi config file with these settings:

```bash
```
```
[device]
wifi.scan-rand-mac-address=no

[connection]
wifi.powersave=2
autoconnect-retries=5
```
```
