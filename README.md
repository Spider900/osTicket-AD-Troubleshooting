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

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/eee96c08-2c20-47bd-9ebb-f46f5a056c97" />

1. Configured support@mydomain.com to be the default support email address for osTicket and configured the remote mailbox

<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/3fbb6aea-f55d-433e-af4c-63083902ecaf" />

2. SMTP configuration settings

<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/77ee42fa-c344-470b-af7e-94f765e1cb86" />

<img width="1916" height="1018" alt="image" src="https://github.com/user-attachments/assets/085a5a7e-e05a-4e9a-98cd-cba3673f659a" />

3. Created autocron script for email fetching and enabled it in Email settings

## Ticketing Functionality Test

<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/a5870519-bfa9-4b10-985b-ba2535d07494" />

1. Home page before ticket creation

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/bf42c979-1e7d-431c-8196-e5990657f311" />

2. Used the email "`p-njoroge@mydomain.com`" to send a ticket to "`support@mydomain.com`". For more information on how I setup my exchange server, see [here](https://github.com/Spider900/exchange-server-lab)

<img width="1918" height="1017" alt="image" src="https://github.com/user-attachments/assets/25767255-2148-47e7-bcdd-91c3f619baaf" />

<img width="1917" height="1021" alt="image" src="https://github.com/user-attachments/assets/59f2c95f-63bb-454d-9761-5409a219d873" />

3. Ticket successfully generated

## AD Troubleshooting Tickets

### Ticket 1 - Account Lockout

<img width="1918" height="1021" alt="T1-1" src="https://github.com/user-attachments/assets/0b9f31c6-5533-4117-babc-bd448d92ba32" />

<img width="1918" height="1023" alt="T1-2" src="https://github.com/user-attachments/assets/69d297de-f840-45e5-8f20-e78e5c9810a9" />

1. User "aabrev" is locked out of their account

<img width="1918" height="1017" alt="image" src="https://github.com/user-attachments/assets/58b1bc53-02ba-418f-a315-b7631b8f4755" />

2. Active Directory Users and Computers reveals the account is locked due to too many login attempts. Selecting "Unlock Account" checkbox and saving the settings will fix the issue.

<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/ef541fe1-6e40-4cfb-974c-e8673f7208de" />

3. Account is no longer locked and user "aabrev" can log on normally
