<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

- 1. Setup Resource in Azure
  - Create the Domain Controller VM (Windows Server 2022) named “DC-1”
  - Take note of the Resource Group and Virtual Network (Vnet) that get created at this time
  - Set Domain Controller’s NIC Private IP address to be static
  - Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in Step 1.a
  - Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher
  
- 2. Ensure Connectivity between the client and Domain Controller
  - Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)
  - Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
  - Check back at Client-1 to see the ping succeed

- 3. Install Active Directory
  - Login to DC-1 and install Active Directory Domain Services, Server Manager > add roles and features ->
  - Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
  - Restart and then log back into DC-1 as user: mydomain.com\labuser
  
  
