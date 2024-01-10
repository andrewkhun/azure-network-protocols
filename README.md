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
<p>
Place the Virtual Machine into the 'RG-Lab' Resource group previously created. Name the VM (Virtual Machine) 'VM-1' and place it into the same region as 'RG-Lab', in this example it is 'West US 3'. Select 'Windows 10 Pro, version 22H2' for the VM Image. 
</p>
<p>
<img src="https://imgur.com/SX6GR61.png" height="70%" width="70%" alt="Create VM 3"/>
</p>
<p>
For 'Size', select '2 vcpus'. Set an Administrator account by creating a username and password. Note the credentials down as we will be using this to log into the VM later. Check the licensing agreement and then make your way to the 'Networking' tab.
</p>
<p>
<img src="https://imgur.com/mYb7SUU.png" height="70%" width="70%" alt="Create VM 3"/>
</p>

<p>
Notice a 'Virtual Network' was automatically created by the VM. We will be using this Virtual Network to view traffic between VM-1 and our second virtual machine, VM-2. After confirming the virtual network has been created, click 'Review + Create' and once validation has passed, select 'Create' and VM-1 will begin setting up.
</p>
<p>
<img src="https://imgur.com/qdo187E.png" height="70%" width="70%" alt="Network Interface"/>
</p>


<br /><h3>Step 3 - Create a Linux Virtual Machine</h3>
<p>
Next we will be creating our second virtual machine. The initial process is the same. Create the VM and place it inside 'RG-Lab' and name it 'VM-2'. Place the VM in the same region as VM-1 and the Resource Group (US West 3).
</p>
<p>
<img src="https://imgur.com/dmV0YNG.png" height="70%" width="70%" alt="Linux VM"/>
</p>
<p>
Select '2 vcpus' for the 'Size'. Check the 'Password' Option for 'Authentication Type' as it is set to 'SSH Public Key' by default, then create a Username and Password and note it down for future use.
</p>
<p>
<img src="https://imgur.com/O1sMvTp.png" height="70%" width="70%" alt="Linux VM"/>
</p>
<p>
In the 'Networking', select the existing 'Virtual Network' that was created during VM-1's setup. This will ensure both VMs are on the same network and can communicate with one another. After confirming this, select 'Review + Create', and if validation has passed, click 'Create' to set up the Linux virtual machine.
</p>
<p>
<img src="https://imgur.com/MJa61Jb.png" height="70%" width="70%" alt="Linux VM"/>
</p>


<br /><h3>Step 4 - Remote into the Windows 10 VM (VM-1)</h3>
<p>In order to remotely conenct into 'VM-1' you must first obtain its 'Public IP Address'. Go to 'Virtual Machines' in the Azure Portal and select 'VM-1'. Copy down the 'Public IP Address' and head back to the desktop.
</p>
<p>
<img src="https://imgur.com/HUe8u4r.png" height="70%" width="70%" alt="Linux VM"/>
</p>
<p>
<img src="https://imgur.com/OIeuXLE.png" height="70%" width="70%" alt="Linux VM"/>
</p>
<p>
In the Windows 'Start' menu, search for 'Remote Desktop Connection'. Input the Public IP Address of VM-1 and click 'Connect'. A prompt will request your credentials, enter the Username and Password created when VM-1 was setup and hit enter. The desktop will setup and you will have successfully logged into the VM.
</p>


<br /><h3>Step 5 - Install Wireshark </h3>
<p>
On VM-1, open up Microsoft Edge and search for and install 'Wireshark'. Download the 'Windows x64 Installer'. Once the download has completed, locate the installer and proceed with installing 'Wireshark' on VM-1.
</p>
<p>
<img src="https://imgur.com/B04C31W.png" height="70%" width="70%" alt="Linux VM"/>
</p>
<p>
<img src="https://imgur.com/GqutGMk.png" height="70%" width="70%" alt="Linux VM"/>
</p>
