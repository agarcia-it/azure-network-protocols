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

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p> 1.) <strong>Create Windows and Linux Virtual Machines - </strong>Within the Microsof Azure Portal, create a Resource Group that will host two virtual machines. Create the two virtual machines: one Windows 10 Pro machine and one Linux Server machine. Ensure thay they both reside within the same Resource Group. Additionally, ensure to create a vnet with the Windows machine, and that the Linux machine has the same vnet. You can inspect the network topology by typing "network watcher" in the Azure search bar -> Network Watcher -> and Topology on the left side of the screen. Select the Resource Group and vnet that hosts both vm's (if there is an error, ensure that the NetworkWatcherRG Resource Group resides within the Resource Group that was created. Your network topology should look like this:
</p>
<p>
<img src="https://i.imgur.com/PH1ezql.png" />
</p>
<br />

<p> <strong></strong>
</p>
<p>
<img src="" />
</p>
<br />
