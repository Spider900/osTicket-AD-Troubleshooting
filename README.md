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

## Ticket 2 - Password Reset

<img width="1918" height="1021" alt="image" src="https://github.com/user-attachments/assets/4a7d8f6d-ec7a-4f75-949e-e6ed3fcedaca" />

<img width="1918" height="1027" alt="image" src="https://github.com/user-attachments/assets/cfb799a5-cb56-4ec2-8a1a-b4f6fb5fae94" />

1. User "aacre" needs their password to be reset

<img width="1918" height="1021" alt="image" src="https://github.com/user-attachments/assets/109f3e84-cd7b-4dff-a065-62fcc6c4457c" />

2. "aacre" will need to enter the temporary password "Password#1" in order to create their new password

<img width="1918" height="1018" alt="T2-4" src="https://github.com/user-attachments/assets/b11ec793-9245-4df8-806b-bd63f4789d30" />

<img width="1918" height="1017" alt="T2-5" src="https://github.com/user-attachments/assets/dc8b30b1-d9b2-4f58-8246-506ab68bf600" />

<img width="1918" height="1018" alt="T2-6" src="https://github.com/user-attachments/assets/3ef807e1-6b5a-4a69-93cd-74165da0e4eb" />

3. Successful password reset

## Ticket 3 - Group Policy Not Applying

<img width="1918" height="1020" alt="T3-1" src="https://github.com/user-attachments/assets/0e13c14b-721e-4f93-af9e-0462e751cb06" />

<img width="1918" height="1018" alt="T3-2" src="https://github.com/user-attachments/assets/e4bd9157-9fa5-4c3a-a78c-00a713d639c5" />

1. Admin "p-njoroge" has an issue with the password changes they implemented applying

<img width="1918" height="1017" alt="T3-3" src="https://github.com/user-attachments/assets/193d0d30-f00c-407b-ab4b-e1a5e2500fb1" />

2. "gpresult /r" reveals over 40 minutes have passed since the last group policy update

<img width="1918" height="1017" alt="T3-4" src="https://github.com/user-attachments/assets/ff31b71d-a897-4759-b549-4d5ab06b7bf7" />

3. Running "gpupdate /force" will push admin's lockout changes

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/2c7003c0-5034-48c1-bb49-4d98c1beeee0" />

4. Accounts now use default Windows 11 lockout settings

## Ticket 4 - User Cannot Log Into Domain

<img width="1918" height="1021" alt="T4-1" src="https://github.com/user-attachments/assets/fb7bee58-cab2-4bd3-a279-89adcc71e594" />

<img width="1918" height="1017" alt="T4-2" src="https://github.com/user-attachments/assets/21899ece-d812-42e4-b400-71e6c7ea1fcc" />

1. User "abargo" is has an issue between the trust relationship of their machine and the DC

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/db191d6b-403e-4b92-88aa-0fa8dafd4ff0" />

2. Re-enabling the domain controlled client machine will fix the error 

## Ticket 5 - Account Expiration

<img width="1918" height="1018" alt="T5-1" src="https://github.com/user-attachments/assets/4104befb-7c1a-4909-a2c0-4d27ad6f7125" />

<img width="1918" height="1020" alt="T5-2" src="https://github.com/user-attachments/assets/5023cd92-89ca-4e3c-aec0-359337c488f6" />

1. Account "Abilderback" has expired and needs to be reactivated

<img width="1919" height="1021" alt="T5-3" src="https://github.com/user-attachments/assets/fd1131bb-1a7c-49b2-abd6-5b5ad5dc898e" />

2. Navigating to AD Users and Computers and setting account expiration to never or a future date will fix the issue

## Ticket 6 - Account Disabled

<img width="1918" height="1021" alt="T6-1" src="https://github.com/user-attachments/assets/e763716c-4782-4be2-91bc-e1d08b12703d" />

<img width="1918" height="1017" alt="T6-2" src="https://github.com/user-attachments/assets/0c25ebe0-3b38-4e95-becf-db1e262f2e58" />

1. User "abirk" reports their account as being disabled

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/81c90db7-93c2-4ee5-876e-13235a69e0fc" />

2. Enabling the account in AD Users and Computers will fix the issue

## Ticket 7 - Folder Permissions

<img width="1918" height="1021" alt="T7-1" src="https://github.com/user-attachments/assets/b6c555b9-11c3-4884-87c8-1ef6c80dfe3e" />

<img width="1918" height="1018" alt="T7-2" src="https://github.com/user-attachments/assets/f157be2a-0da8-45e8-902b-c05a0dd33140" />

1. User "ablackwater" unfortunately cannot add cute pictures of their dog to the shared puppies folder

<img width="1918" height="1017" alt="T7-3" src="https://github.com/user-attachments/assets/c143a17b-5945-4ce7-a7ab-d9996a3cdd3b" />

2. The shared permissions on the folder only grant read access to users which is causing the problem

<img width="1918" height="1018" alt="T7-4" src="https://github.com/user-attachments/assets/7fa6f6bb-bc92-4a50-b713-d5342925a94b" />

<img width="1918" height="1020" alt="T7-5" src="https://github.com/user-attachments/assets/99ec08c8-b2a7-45e1-a211-a8a5d9c87d06" />

3. Enabling Read/Write will fix the issue

<img width="1918" height="1017" alt="T7-6" src="https://github.com/user-attachments/assets/e72a6d53-d570-4bbc-847d-9311d670a44e" />

4. User "ablackwater" now has the permissions to access the folder
