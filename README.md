<img width="2000" height="500" alt="pihole homelab banner" src="https://github.com/user-attachments/assets/1e8d036c-bd7f-4292-a72d-6e36283ddf42" />

# Pi-hole Deployment Homelab

## A self-hosted Pi-hole deployment running on a Linux-based homelab server used for network-wide DNS filtering, ad blocking, and LAN management.

## Project Overview

This project involved deploying and configuring a self-hosted Pi-hole DNS filtering server within a homelab environment. The server was used to provide network-wide ad blocking, DNS filtering, and traffic visibility for multiple connected devices across the local network.

The deployment was configured on a Linux-based system and integrated with the home router to manage DNS requests for LAN-connected devices.


## Objectives

- Deploy Pi-hole in a home network environment
- Configure custom DNS and DHCP settings
- Reduce ads and across network devices
- Learn Linux server administration and networking
- Troubleshoot DNS and connectivity issues

## Technologies Used

- Pi-hole
- Kubuntu
- DNS
- DHCP
- SSH
- Linux CLI
- Home networking


<img width="1000" height="1000" alt="pihole homelab graphic 2" src="https://github.com/user-attachments/assets/f5376c7c-2ae0-4665-86ce-7e3d01518bc9" />




## Skills Demonstrated

- Linux Administration
- DNS Configuration
- Network Troubleshooting
- SSH Remote Management
- Homelab Infrastructure
- Router Configuration
- Service Deployment
- Documentation

## Challenges Encountered with solutions

### Kubuntu installed without Wi-Fi firmware/drivers
- Reinstalled Kubuntu multiple times
- Connected temporarily through phone tethering
- Installed firmware/packages manually

### Realtek RTL8822CE Wi-Fi adapter issues
- Verified driver: rtw88_8822ce
- Reloaded modules repeatedly
- Eventually discovered hardware/driver was not the root issue

### No internet access during setup
- Connected laptop to phone hotspot/tethering

### Git clone hanging/timeouts
- Retried repeatedly after restoring temporary internet access

### "Unable to locate package" errors
- Ran: sudo apt update
- Reinstalled/changed Linux installs multiple times

### Endless KDE Daemon password prompts
- Attempted disabling KWallet
- Attempted removing KWallet
- Attempted replacing secret-service handling
- Eventually realized prompts were caused by failed authentication attempts

### KWallet missing or improperly configured
- Reinstalled wallet-related packages
- Attempted enabling wallet subsystem manually

### GNOME Keyring conflicting with KWallet
- Identified: org.freedesktop.secrets
- Attempted disabling GNOME Keyring services

### D-Bus / Secret Service conflicts
- Masked/stopped multiple wallet/keyring services
- Created dummy org.freedesktop.secrets override

### Incorrect KWallet password
- Deleted old wallet files
- Recreated wallet

### "Waiting for authentication" Wi-Fi loop
- Deleted old Wi-Fi connection profiles
- Reconnected through nmcli and GUI repeatedly

### "No secret key" NetworkManager error
- Connected directly through: nmcli dev wifi connect "SSID" password "PASSWORD"

### Broken/incomplete Wi-Fi connection profiles
- Removed broken .nmconnection files
- Rebuilt connection profiles from scratch

### Same issue reproduced on Fedora KDE
- Installed Fedora KDE to test if Kubuntu was the problem
- Confirmed issue persisted across distros

### Devices bypassing Pi-hole DNS
- Checked DNS using: nslookup
- Found Comcast/Xfinity DNS: 75.75.75.75
- Began reconfiguring DNS routing

### Pi-hole dashboard not receiving queries
- Determined devices were not using Pi-hole as DNS yet

### Router DNS / DHCP confusion
- Researched router-level DNS assignment
- Planned to point router DHCP DNS toward Pi-hole IP

## Future Improvements

- Add VLAN segmentation
- Deploy redundant DNS failover
- Implement containerized deployment
- Add monitoring dashboards
- Configure automated backups












