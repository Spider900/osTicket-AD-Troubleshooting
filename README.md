# 🎫 Home Lab: osTicket Help Desk Troubleshooting

## Overview
I deployed osTicket on a Ubuntu Server VM and connected it to my existing Active Directory environment. The osTicket site is served over an HTTPS connection which is verified by an SSL certificate issued by the internal Certificate Authority on my Domain Controller. This lab also demonstrates a complete IT help desk workflow, from ticket intake to resolution, using ten real AD troubleshooting scenarios. For further documentation on my previous AD lab, see it [here](https://github.com/Spider900/ad-windows-server-lab).

![Badge](https://img.shields.io/badge/Ubuntu_Server_22.04-orange) ![Badge](https://img.shields.io/badge/osTicket_1.18-yellow) ![Badge](https://img.shields.io/badge/Active_Directory-purple) ![Badge](https://img.shields.io/badge/LAMP_Stack-green) ![Badge](https://img.shields.io/badge/VirtualBox-grey) ![Badge](https://img.shields.io/badge/Internal_PKI_Certified-red)

## Architecture
| Component | Details |
| --------- | ------- |
| Help Desk Server | Ubuntu Server 22.04 + osTicket 1.18.3 |
| Domain Controller | Windows Server 2019 (existing AD lab) |
| Client Machine  | Windows 11 (domain-joined) |
| Hypervisor | Oracle VirtualBox |
| Network Adapter | Internal Network |
| osTicket URL | `https://172.16.0.101/scp/` |
| Web Stack | Apache, MySQL, PHP (LAMP) |

## Features Implemented

✅ Ubuntu Server deployed as a dedicated VM on internal network

✅ LAMP stack installed and configured (Apache, MySQL, PHP)

✅ osTicket installed and accessible from domain-joined client

✅ osTicket integrated with Active Directory for user authentication

✅ SSL certificate issued by internal CA on Domain Controller

✅ Apache configured to serve osTicket over HTTPS

✅ Help desk agents and departments configured in osTicket

✅ 10 tickets created and resolved covering common AD issues

## Settings and Configuration

### SSL Certificate

<img width="1918" height="1021" alt="image" src="https://github.com/user-attachments/assets/81c75c25-4cdb-4040-9ce6-4c95bac6b153" />

1. SSL certificate issued by internal CA on Domain Controller for the osTicket server

<img width="1918" height="1025" alt="image" src="https://github.com/user-attachments/assets/e24a463f-4fad-4254-acbd-ea471a37311f" />

2. Transfered SSL certificate to a cert file on my linux server
 
### Apache HTTPS Configuration

<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/0299206b-0ac1-4aff-9ae2-6ca8ae161b5d" />

1. Apache virtual host configured to HTTPS port 443 with paths to internal SSL certificate and key

### osTicket accessible over HTTPS

<img width="1918" height="1017" alt="image" src="https://github.com/user-attachments/assets/e77d0ec4-1927-40c9-b00e-69311654e033" />

1. osTicket site is secure through https and osTicket cert is confirmed by the Domain Controller

### Active Directory Integration

<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/d016adc8-f1df-45d4-812c-981f4e2de4fe" />

1. osTicket configured to authenticate against mydomain.com

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/c90d805b-b452-4133-887a-6e554ed9eeb6" />

<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/583927ab-25d9-4626-9791-dd6bf483bc81" />

<img width="1918" height="1027" alt="image" src="https://github.com/user-attachments/assets/09c046a0-0575-4bf1-8c08-9fddfa35a31b" />

2. Created agent accounts are automatically synced to their respective AD account

### osTicket Email Fetching

