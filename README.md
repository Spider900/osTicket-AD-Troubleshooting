# 🎫 Home Lab: osTicket Help Desk + Active Directory Integration

## Overview
I deployed osTicket on a Ubuntu Server VM and connected it to my existing Active Directory environment. This lab demonstrates a full IT help desk workflow, from ticket intake to resolution. Each of the 10 tickets represents a common issue encountered in enterprise AD environments, documented with root cause analysis and resolution steps. For further documentation on my AD lab, see it [here](https://github.com/Spider900/ad-windows-server-lab).

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
