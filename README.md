<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Virtual Machines in Azure.
- Observe ICMP traffic between Virtual Machines using Wireshark.
- Configure a Firewall (Network Security Group) analyze its impact on network traffic
- Observe various protocol traffic (SSH, DHCP,DNS,RDP) using Wireshark.

<h2>Actions and Observations</h2>

Part 1: Create Virtual Machines 
- Log into Azure Portal
- Create a Resource Group
  1.) Navigate to "Resource Groups" and click on create.
  2.) provide a name for your Resource Group and select a region.
  3.) Click "Review + Create" then "Create."

  ![image](https://github.com/user-attachments/assets/031bb56d-4d48-4610-b8ed-f849d6c789a7)

Create a Windows 10 Virtual Machine 
- Navigate to "Virtual Machines" and click "Create"
- Select the Resource Group you just created.
- Configure the Virtual Machine.
- OS: Windows10
- Create usrname and password
- Head to the network titled "Lab2-vnet.
- Complete the setup and deploy the VM.

  ![image](https://github.com/user-attachments/assets/946e3375-08e4-48a3-8249-b3bff92c0c90)

  ![image](https://github.com/user-attachments/assets/967e3c27-25d4-4728-80b6-bb7b80abba83)

  ![image](https://github.com/user-attachments/assets/df6b052a-0b31-4a1b-a785-bc96662a7ee9)

  ![image](https://github.com/user-attachments/assets/fbd6de41-b8a6-472a-be64-048c7bf82a6b)

  Create a Linux (Ubuntu) Virtual Machine
  - Navigate to "Virtual Machines" and click "Create"
  - Select the same Resource Group and Virtual Network used for the Windows10 VM
  - Configure the Virtual Machine
  - OS: Ubuntu server 22.04
  - Create username and password
  - Ensure both VMS are in the same Virtual Network and Subnet as the Windows10 VM
  - Complete the setup and deploy the VM

    ![image](https://github.com/user-attachments/assets/e9bb3ab2-4196-46af-9346-ff55f387c893)

    ![image](https://github.com/user-attachments/assets/3eafe6c6-abec-4577-93c2-f59058379b41)

    ![image](https://github.com/user-attachments/assets/ff609b2e-8911-4986-90a4-b63251680dab)

    ![image](https://github.com/user-attachments/assets/aa739f1a-7d1f-4365-8b86-5219dcfa7cb5)

    Part2: Observe ICMP Traffic

    1.) Use Microsoft Remote Desktop to connect to your Windows10 Virtual Machine.
    2.) Install Wireshark on the Windows10 VM
    3.) Open Wireshark and start a packet capture
    4.) Filter for ICMP traffic in Wireshark
    5.) Retrieve the private IP address of the UBUNTU VM and attempt to ping it from the Windows10 VM
    - Open command prompt or powershell and run ping <Ubuntu vm private IP>
    - Observe the ping requests and replies in Wireshark
    6.) From the Windows10 VM ping a public website (e.g., www.google.com) and observe ICMP traffic in Wireshark

      









<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
