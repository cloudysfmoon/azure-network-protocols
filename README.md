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
We are using a Mac so we will need to go to the App Store and download Microsoft Remote Desktop(Windows App) to connect to the remote desktop. We will need to use the IP address of the windows virtual machine to connect, as well as the adminstrator credentials to be able to login to the machine.

![2](https://github.com/user-attachments/assets/4efe87e8-0a4b-4b6b-8324-94f50fedcc6b)
<p>
  
![3](https://github.com/user-attachments/assets/60166c69-584f-4994-8b27-1f6787702fc4)
<p>
We are going to download an application from the Windows virtual machine called Wireshark, which is a network protocol analyzer. To analyze network traffic using Wireshark, we first opened the application and initiated a packet capture. To focus on relevant data, we applied a filter to display only ICMP (Internet Control Message Protocol) traffic. Next, we identified the private IP address of the Ubuntu virtual machine (which was 10.0.0.5) and attempted to ping it from the Windows 10 VM. This allowed us to observe the ping requests and responses within Wireshark, confirming network communication between the two VMs. 

![7](https://github.com/user-attachments/assets/ffa6bb6a-4fc2-486c-a44f-4c6eac09dbd1)
<p>
Configuring a Firewall [Network Security Group]
To test network security settings, we first started a continuous (-t) ping from the Windows 10 VM to the Ubuntu VM. While the ping was running, we accessed the Network Security Group (NSG) for the Ubuntu VM and disabled inbound ICMP traffic. Back in the Windows 10 VM, we observed the ping responses in the command line and Wireshark, noticing that the requests were being sent but no replies were received. Then, we re-enabled ICMP traffic in the NSG and saw the ping responses resume in both the command line and Wireshark, confirming that the Ubuntu VM was reachable again. Finally, we stopped the ping activity.

![8](https://github.com/user-attachments/assets/ee571524-db2f-4f36-8aa5-c57325d72a1a)
<p>
  
![9](https://github.com/user-attachments/assets/5dcdcfdc-45db-40e4-a671-c37051b0c400)
<p>
  
![10](https://github.com/user-attachments/assets/34a8ac64-2490-482d-8945-9946bcfa07b2)
As we can see the request timed out due to the security ruled we added so the linux virtual machine is ignoring the traffic causing the time out request and not replying to the traffic. 
<p>
Observing SSH Traffic
<p>
We will be observing SSH traffic in Wireshark, we need to filter by SSH in the program, it will also requre to input the admin credentials in order to continue in order to observe the traffic. 

![1](https://github.com/user-attachments/assets/3999073b-58ad-48b8-9e0b-67164672820f)
<p>

![2](https://github.com/user-attachments/assets/79cdb91a-0a63-486d-a9aa-b45b5a5780f9)
<p>
Observing DHCP Traffic
<p>
In this section, we obseved the traffic for DHCP. we filtered for DHCP traffic, specifcally we filtered by the UDP ports(67,68). We had to create a bat file and save it to the Program Data section in the Windows VM, due to when we first ran ipconfig /release, it crashed the virtual machine. The reason we ran the commands using a bat file is beacuse it runs the commands sequentially. 

![3](https://github.com/user-attachments/assets/576a74be-1545-41ed-8801-f30a6ace9ec3)
<p>
  
![5](https://github.com/user-attachments/assets/242e9a87-a062-404c-9057-e9e178d1ba62)
<p>

![6](https://github.com/user-attachments/assets/9e5d1883-2a2b-4a21-a3ed-a9491a8fcf69)
<p>
Now we are able to see the different DHCP traffic in Wireshark.
<p>
Observing DNS Traffic
<p>
The DNS lookup is easier, we filter by DNS in Wireshark and we are abe to see the traffic from websites once we input "nslookup" and the website that follows, fort example, we used Disney and Goolge and we were able to see their addresses. 

![1 dns lookup](https://github.com/user-attachments/assets/8f7a182f-f585-4753-925b-c4edaad0346d)
<p>
Observing RDP Traffic
<p>
We filter in Wireshark for RDP traffic only (tcp.port == 3389). The traffic is still only non-stop spamming. The reason is because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted.

![rdp traffic 1](https://github.com/user-attachments/assets/1145dd5c-d879-44b8-ab07-ca8301acdd5a)
<p>
<br />
