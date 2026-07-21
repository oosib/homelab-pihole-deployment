<img width="2000" height="400" alt="pihole homelab banner" src="https://github.com/user-attachments/assets/1e8d036c-bd7f-4292-a72d-6e36283ddf42" />

![Kubuntu](https://img.shields.io/badge/-KUbuntu-%230079C1?style=for-the-badge&logo=kubuntu&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Pi-Hole](https://img.shields.io/badge/pihole-%2396060C.svg?style=for-the-badge&logo=pi-hole&logoColor=white)
![Static Badge](https://img.shields.io/badge/HOMELAB-badge?style=for-the-badge&logoSize=500&color=%2360ee59)
![Static Badge](https://img.shields.io/badge/DNS-badge?style=for-the-badge&logoSize=500&color=%23e6b400)
![Static Badge](https://img.shields.io/badge/SELF--HOSTED-badge?style=for-the-badge&logoSize=500&color=%230077b6)
![Static Badge](https://img.shields.io/badge/DHCP-badge?style=for-the-badge&logoSize=500&color=%23800080)



# Project Overview

<table>
  <tr>
    <td width="50%" valign="top">

<p>
This project involved deploying and configuring a self-hosted Pi-hole DNS
filtering server within a homelab environment. The server was used to provide
network-wide ad blocking, DNS filtering, and traffic visibility for multiple
connected devices across the local network.
</p>

<p>
The deployment was configured on a Linux-based system and integrated with the
home router to manage DNS requests for LAN-connected devices.
</p>
    </td>
    <td width="50%" valign="top">

<p align="center">
<strong>Network Architecture</strong>
</p>

<div align="center">
<img
  width="430"
  alt="Pi-hole Homelab Network Architecture"
  src="https://github.com/user-attachments/assets/f5376c7c-2ae0-4665-86ce-7e3d01518bc9">
</p>
    </td>
  </tr>
</table>

# 🎯Objectives

- Deploy Pi-hole in a home network environment
- Configure custom DNS and DHCP settings
- Reduce ads and across network devices
- Learn Linux server administration and networking
- Troubleshoot DNS and connectivity issues

# Skills Demonstrated

- Linux Administration
- DNS Configuration
- Network Troubleshooting
- SSH Remote Management
- Homelab Infrastructure
- Router Configuration
- Service Deployment
- Documentation






## Deployment Overview

<img width="1000" height="550" alt="Screenshot 2026-07-21 165124" src="https://github.com/user-attachments/assets/ba9b95f9-890e-4dd6-a785-df38751368f2" />

Dashboard captured after little over a day of operation with multiple LAN devices configured to use Pi-hole for DNS resolution.

## Deployment Highlights

| Query Statistics | Top Clients |
| --- | --- |
| <img width="950" height="200" alt="image" src="https://github.com/user-attachments/assets/1a25bd4e-94e7-4d5f-b01f-f8a6846e0392" /> | <img width="969" height="249" alt="pihole top clients 2 blurred" src="https://github.com/user-attachments/assets/17cc97d5-94b0-417f-84f1-3125ffa7e73c" /> |
| <img width="1000" height="300" alt="Screenshot 2026-07-21 165334" src="https://github.com/user-attachments/assets/68361142-1cec-484e-8aea-9ff5f2551dad" /> | <img width="972" height="309" alt="pihole top clients blurred" src="https://github.com/user-attachments/assets/619337d6-5e2d-46f0-8579-bedc28030e03" />|
| Total and blocked DNS queries recorded by Pi-hole. | Top devices actively resolving DNS through the server. |

| Query Log | Blocklists |
| --- | --- |
| <img width="972" height="558" alt="image" src="https://github.com/user-attachments/assets/6816b5d7-8a27-4217-b1cb-104972544ca3" />| <img width="981" height="425" alt="piholeblocklist blurred" src="https://github.com/user-attachments/assets/150b0147-51de-417d-bddc-23752f224abe" /> |
| Live view of allowed and blocked requests. | Active lists used for filtering coverage. |










# 💡Troubleshooting Highlights
"Highlights" may be a generous description—these are the issues that took the longest to diagnose and ultimately taught me the most.




## Pi-hole Receiving No DNS Queries
<details>
  <summary>Click here for details</summary>
<h3><strong>❓ What was the challenge?</strong></h3>  
  
  After completing the Pi-hole deployment, the dashboard showed little to no DNS activity despite multiple devices being connected to the network. Although the Pi-hole services were running correctly, client devices were not sending DNS requests to the server.

 <h3><strong>✅ What was the resolution? </strong></h3>
 
I verified that the Pi-hole services were operational, reviewed client network configurations, and used DNS lookup tools to determine which DNS servers devices were using. Identified that clients were still resolving through the router's default DNS servers, updated the network configuration to direct DNS traffic through Pi-hole, and confirmed successful operation by monitoring live query activity.
</details>




## Router DNS / DHCP Configuration
<details>
  <summary>Click here for details</summary>
<h3><strong>❓ What was the challenge?</strong></h3>
  
Determining where DNS should be configured within the network proved challenging due to the interaction between the router's DHCP service and client devices. Incorrect DNS assignment prevented devices from automatically using the Pi-hole server.

<h3><strong>✅ What was the resolution? </strong></h3>

Researched the router's DHCP and DNS configuration, evaluated how DNS settings were distributed to connected devices, and updated the network configuration so clients received the Pi-hole server as their primary DNS resolver. Verified proper configuration by confirming client devices were resolving requests through Pi-hole.
</details>




## Pi-hole Admin Interface Returning 403 Forbidden
<details>
  <summary>Click here for details</summary>
<h3><strong>❓ What was the challenge?</strong></h3>
  
Following installation, the Pi-hole web administration interface became inaccessible and returned a 403 Forbidden error despite the underlying Pi-hole services remaining active.

<h3><strong>✅ What was the resolution? </strong></h3>

Verified the status of the Pi-hole services, inspected the web server configuration, reviewed file permissions, and validated the installation. After correcting the web interface configuration, access to the Pi-hole dashboard was restored and functionality was confirmed.
</details>




## Kubuntu Installed Without Wi-Fi Support
<details>
  <summary>Click here for details</summary>
<h3><strong>❓ What was the challenge?</strong></h3>
  
The initial Kubuntu installation completed successfully but lacked the required wireless firmware, preventing the system from connecting to the internet and downloading the packages needed to continue the deployment.

<h3><strong>✅ What was the resolution? </strong></h3>

Established a temporary network connection using USB phone tethering, manually installed the required firmware packages, and verified wireless functionality before proceeding with the Pi-hole deployment.
</details>



## Realtek RTL8822CE Wi-Fi Driver Investigation
<details>
  <summary>Click here for details</summary>
<h3><strong>❓ What was the challenge?</strong></h3>
  
Wireless connectivity issues initially appeared to be caused by the Realtek RTL8822CE adapter or its Linux driver. Multiple symptoms suggested a driver-related problem, including repeated authentication failures and inconsistent network behavior.

<h3><strong>✅ What was the resolution? </strong></h3>

Validated the installed driver, tested alternative driver configurations, and compared behavior across multiple Linux distributions. Continued investigating beyond the initial assumption until determining that the wireless adapter and driver were not the root cause, allowing troubleshooting efforts to shift toward the actual configuration issue.
</details>



# Future Improvements

- Add VLAN segmentation
- Deploy redundant DNS failover
- Implement containerized deployment
- Add monitoring dashboards
- Configure automated backups


## Final Thoughts

This project started as a way to learn Linux networking and self-hosted infrastructure, but it quickly became an exercise in troubleshooting. Solving these issues required researching documentation, testing different approaches, validating assumptions, and learning how DNS and network services interact. While the deployment itself was the objective, the troubleshooting process provided the most valuable experience.







