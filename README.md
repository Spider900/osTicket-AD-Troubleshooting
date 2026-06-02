# 🎫 Home Lab: osTicket Help Desk Troubleshooting

## Overview
I deployed osTicket on a Ubuntu Server VM and connected it to my existing Active Directory environment. This lab demonstrates a full IT help desk workflow, from ticket intake to resolution. Each of the 10 tickets represents a common issue encountered in enterprise AD environments, documented with root cause analysis and resolution steps. For further documentation on my AD lab, see it [here](https://github.com/Spider900/ad-windows-server-lab).

![Badge](https://img.shields.io/badge/Ubuntu_Server_22.04-orange) ![Badge](https://img.shields.io/badge/osTicket_1.18-yellow) ![Badge](https://img.shields.io/badge/Active_Directory-purple) ![Badge](https://img.shields.io/badge/LAMP_Stack-green) ![Badge](https://img.shields.io/badge/VirtualBox-grey)

## Architecture
| Component | Details |
| --------- | ------- |
| Help Desk Server | Ubuntu Server 22.04 + osTicket 1.18.3 |
| Domain Controller | Windows Server 2019 (existing AD lab) |
| Client Machine  | Windows 11 (domain-joined) |
| Hypervisor | Oracle VirtualBox |
| Network Adapter | Internal Network |
| osTicket URL | `http://172.16.0.101/scp/` |
| Web Stack | Apache, MySQL, PHP (LAMP) |

## Features Implemented

✅ Ubuntu Server deployed as a dedicated VM on internal network

✅ LAMP stack installed and configured (Apache, MySQL, PHP)

✅ osTicket installed and accessible from domain-joined client

✅ osTicket integrated with Active Directory for user authentication

✅ Help desk agents and departments configured in osTicket

✅ 10 tickets created and resolved covering common AD issues

✅ Root cause and resolution documented for each ticket

