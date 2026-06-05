# 🎫 Home Lab: osTicket Help Desk Troubleshooting

## Overview
I deployed osTicket on a Ubuntu Server VM and connected it to my existing Active Directory environment. The osTicket site is served over HTTPS using an SSL certificate issued by the internal Certificate Authority on my Domain Controller — mirroring how enterprise help desk portals are secured in real environments. This lab demonstrates a full IT help desk workflow — from ticket intake to resolution — using ten real AD troubleshooting scenarios. For further documentation on my AD lab, see it [here](https://github.com/Spider900/ad-windows-server-lab).

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

