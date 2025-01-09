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
    6.) From the Windows10 VM ping a public website (e.g., www.disney.com) and observe ICMP traffic in Wireshark

     ![image](https://github.com/user-attachments/assets/6b950b8e-1c5a-4604-ad3e-9b87cd0ddafd)
 
![image](https://github.com/user-attachments/assets/034f56f6-7a57-4847-b74f-a9685d786223)


Part 3: Configure a Firewall (Network Security Group)

1. Initiate a continuous ping from your Windows10 VM to the unbuntu VM
2. Open the Network security Group associated with the unbuntu VM
3. Disable inbound ICMP traffic in the Network Security Group
4. Observe the ICMP traffic in Wireshark and the command line ping should stop
5. Re-enable ICMP traffic in the Network Security Group
6. Observe the ICMP traffic in Wireshark and the command line ping should resume
7. Stop the ping activity

   Observe SSH Traffic 

1. In Wireshark start a new packet capture and filter for SSH traffic
2. From the Windows10 VM, SSH into the Unbuntu VM
   -Command: SSH <Username>@<Unbuntu VM Private IP
   - Enter the Password when prompted
3. Type commands within the SSH session and observe the SSH traffic in Wireshark
4. Exit the SSH session: EXIT

 ![image](https://github.com/user-attachments/assets/d8486176-b867-40d9-b960-4c66a4a2777d)

 ![image](https://github.com/user-attachments/assets/b5979e07-4a9b-4086-b668-aff91c146855)

 Observe DHCP Traffic

 1. In Wireshark filter for DHCP traffic
 2. From the Windows10 VM issue a new IP address
    -Open PowerShell as admin and run: ipconfig/renew
 3. Observe the DHCP traffic in Wireshark

    ![image](https://github.com/user-attachments/assets/94ecd319-3a78-4673-98bf-c82a60a933bc)

Observe DNS Traffic

1. In Wireshark filter for DNS traffic
2. From the Windows10 VM use nslookup to find the IP addresses for websites
   - example : nslookup disney.com, nslookup google.com
3. Observe the DNS traffic in Wireshark

![image](https://github.com/user-attachments/assets/07d119e0-c21c-44dc-9ff7-75bbdf303d59)

Observe RDP Traffic 

1. In Wireshark filter for RDP traffic
   - Use the filter: tcp.port==3389
2. Observe the continuous RDP traffic between the Windows 10 VM and your local machine
  
![image](https://github.com/user-attachments/assets/f733a194-edc6-452e-bd94-9257f66cce73)


  

