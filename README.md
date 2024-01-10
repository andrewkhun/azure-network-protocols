<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.<br /><br />

Please note in order to complete this lab you must create a Microsoft Azure account and have an active subscription!

<br /><h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (ICMP, RDP, SSH, DHCP, DNS)
- Wireshark (Protocol Analyzer)

<br /><h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<br /><h2>High-Level Steps</h2>

- Step 1 - Make a Resource Group
- Step 2 - Create a Windows VM
- Step 3 - Create a Linux VM
- Step 4 - Remote Desktop into the Windows VM
- Step 5 - Install Wireshark
- Step 6 - Observe ICMP Traffic
- Step 7 - Access Network Security Group
- Step 8 - Observe SSH Traffic
- Step 9 - Observe DHCP Traffic
- Step 10 - Observe DNS Traffic
- Step 11 - Observe RDP Traffic
- Step 12 - Clean Up Resources


<br /><h3>Step 1 - Make a Resource Group</h3>
<p>
In the Azure Portal go to 'Resouce Groups' to create a new Resource Group and name it 'RG-Lab'. Take note of the region of the Resource Group as we will place our virtual machines in the same region to keep things consistent.
</p>
<p>
<img src="https://imgur.com/Cv80sML.png" height="70%" width="70%" alt="Resource Group 1"/>
</p>
<p>
<img src="https://imgur.com/0yFJfwV.png" height="70%" width="70%" alt="Resource Group 2"/>
</p>
<p>
<img src="https://imgur.com/H8YRCCo.png" height="70%" width="70%" alt="Resource Group 3"/>
</p>




<br /><h3>Step 2 - Create a Windows 10 Virtual Machine</h3>
<p>
After creating the Resource Group, go to 'Virtual Machines' and click 'Create' to create an Azure Virtual Machine.
</p>
<p>
<img src="https://imgur.com/A0nM8G5.png" height="70%" width="70%" alt="Create VM 1"/>
</p>
<p>
<img src="https://imgur.com/uSSHRJb.png" height="70%" width="70%" alt="Create VM 2"/>
</p>
<br /><p>
Place the Virtual Machine into the 'RG-Lab' Resource group previously created. Name the VM (Virtual Machine) 'VM-1' and place it into the same region as 'RG-Lab', in this example it is 'West US 3'. Select 'Windows 10 Pro, version 22H2' for the VM Image. 
</p>
<p>
<img src="https://imgur.com/SX6GR61.png" height="70%" width="70%" alt="Create VM 3"/>
</p>
<br /><p>
For 'Size', select '2 vcpus'. Set an Administrator account by creating a username and password. Note the credentials down as we will be using this to log into the VM later. Check the licensing agreement and then make your way to the 'Networking' tab.
</p>
<p>
<img src="https://imgur.com/mYb7SUU.png" height="70%" width="70%" alt="Create VM 3"/>
</p>



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
