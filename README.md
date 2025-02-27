<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Creating the Virtual Machines
- Observing ICMP Traffic
- Configuring a Firewall [Network Security Group]
- Observing SSH Traffic
- Observing DHCP Traffic
- Observing DNS Traffic
- Observing RDP Traffic

<h2>Actions and Observations</h2>
Creating the Virtual Machines
<p>
We used Azure to create our virtual machines, we first created our resource group for our virtual machines, we need a Windows virtual machine and a Linux virtual machine. The virtual machines will be differentiaed by windows-vm and, linux-vm, all of the regions will need to be on US East 2.
  
![2](https://github.com/user-attachments/assets/f578b0da-72f3-4c29-9898-a55013963253)


![7](https://github.com/user-attachments/assets/a3b53b50-23e2-40af-8dce-cd1b4989f45b)

<p>
We need to make sure we have an adminstrator set up for the virtual machine, we need a username and a password to coincide with everything. 
  
![4](https://github.com/user-attachments/assets/190df94b-86b5-4c5b-944b-e791b5bf177f)
<p>
Next we will set up the virtual network which will be done for both the Windows and Linux virtual machines.

![5](https://github.com/user-attachments/assets/c0097400-4700-467c-b48a-132f32922830)
<p>
Observing ICMP Traffic
<p>













<br />

<p>

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
