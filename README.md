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


<img width="2000" height="2000" alt="pihole homelab graphic 2" src="https://github.com/user-attachments/assets/f5376c7c-2ae0-4665-86ce-7e3d01518bc9" />




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

1. Kubuntu installed without Wi-Fi firmware/drivers
Solution:
- Reinstalled Kubuntu multiple times
- Connected temporarily through phone tethering
- Installed firmware/packages manually

# 2. Realtek RTL8822CE Wi-Fi adapter issues
Solution:
- Verified driver:
-- rtw88_8822ce
- Reloaded modules repeatedly
- Eventually discovered hardware/driver was not the root issue

3. No internet access during setup
# Solution:
- Connected laptop to phone hotspot/tethering

4. Git clone hanging/timeouts
# Solution:
- Retried repeatedly after restoring temporary internet access

5. "Unable to locate package" errors
# Solution:
# - Ran:
#   sudo apt update
# - Reinstalled/changed Linux installs multiple times

# 6. Endless KDE Daemon password prompts
# Solution:
# - Attempted disabling KWallet
# - Attempted removing KWallet
# - Attempted replacing secret-service handling
# - Eventually realized prompts were caused by failed authentication attempts

# 7. KWallet missing or improperly configured
# Solution:
# - Reinstalled wallet-related packages
# - Attempted enabling wallet subsystem manually

# 8. GNOME Keyring conflicting with KWallet
# Solution:
# - Identified:
#   org.freedesktop.secrets
# - Attempted disabling GNOME Keyring services

# 9. D-Bus / Secret Service conflicts
# Solution:
# - Masked/stopped multiple wallet/keyring services
# - Created dummy org.freedesktop.secrets override

# 10. Incorrect KWallet password
# Solution:
# - Deleted old wallet files
# - Recreated wallet

# 11. Incorrect Wi-Fi password entered repeatedly 😄
# Solution:
# - Finally entered correct Wi-Fi password
# - Realized this was the primary root cause

# 12. "Waiting for authentication" Wi-Fi loop
# Solution:
# - Deleted old Wi-Fi connection profiles
# - Reconnected through nmcli and GUI repeatedly

# 13. "No secret key" NetworkManager error
# Solution:
# - Connected directly through:
#   nmcli dev wifi connect "SSID" password "PASSWORD"

# 14. Broken/incomplete Wi-Fi connection profiles
# Solution:
# - Removed broken .nmconnection files
# - Rebuilt connection profiles from scratch

# 15. Same issue reproduced on Fedora KDE
# Solution:
# - Installed Fedora KDE to test if Kubuntu was the problem
# - Confirmed issue persisted across distros

# 16. Devices bypassing Pi-hole DNS
# Solution:
# - Checked DNS using:
#   nslookup
# - Found Comcast/Xfinity DNS:
#   75.75.75.75
# - Began reconfiguring DNS routing

# 17. Pi-hole dashboard not receiving queries
# Solution:
# - Determined devices were not using Pi-hole as DNS yet

# 18. Router DNS / DHCP confusion
# Solution:
# - Researched router-level DNS assignment
# - Planned to point router DHCP DNS toward Pi-hole IP

## Future Improvements

- Add VLAN segmentation
- Deploy redundant DNS failover
- Implement containerized deployment
- Add monitoring dashboards
- Configure automated backups
