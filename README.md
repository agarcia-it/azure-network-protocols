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

<p> 1.) <strong>Create Windows and Linux Virtual Machines - </strong>Within the Microsof Azure Portal, create a Resource Group that will host two virtual machines. Create the two virtual machines: one Windows 10 Pro machine and one Linux Server machine. Ensure thay they both reside within the same Resource Group. Additionally, ensure to create a vnet with the Windows machine, and that the Linux machine has the same vnet. You can inspect the network topology by typing "network watcher" in the Azure search bar -> Network Watcher -> and Topology on the left side of the screen. Select the Resource Group and vnet that hosts both vm's (if there is an error, ensure that the NetworkWatcher_*yourregion* resides within the Resource Group that you created. Your network topology should look like this:
</p>
<p>
<img src="https://i.imgur.com/PH1ezql.png" />
</p>
<p>---------------------------------------------------------------------------------------------------------------------------------</p>
<br />

<p> 2.) <strong>RDP Into Windows VM and Observe Network Traffic - </strong>Use Remote Desktop and the public IP address to remotely sign into and control the Windows VM. Once inside, open an Edge browser, search "wireshark download", and then download and install the 64-bit Windows Wireshark client with all default settings. Once installed, open Wireshark, click the blue shark fin in the top-left of the window and observe the network traffic. There should be constant influx of network traffic from various ports and protocols.
</p>
<p>
<img src="https://i.imgur.com/9QdWUGy.png" />
</p>
<p>---------------------------------------------------------------------------------------------------------------------------------</p>
<br />

<p> 3.) <strong>Filter for IMCP Traffic and Ping the Linux vm - </strong>Within Wireshark, type "icmp", click icmp in the drop down menu, and press enter. Now Wireshark is only filtering for ICMP traffic. The ICMP protocol hosts the ping command, and should allow us to see any ping traffic between our Windows vm and the Linux vm. To do this, find the Public IP address for the Linux VM within Azure. Open a Command Prompt in the Windows vm and type "ping 20.169.165.95 -t" (use the Public IP from your Linux VM as it will be different from mine). This will create a perpetual ping to the Linux VM, and we should only see requests and no replies, meaning the two vms are not yet communicating.
</p>
<p>
<img src="https://i.imgur.com/1c1K960.png" />
</p>
<p>---------------------------------------------------------------------------------------------------------------------------------</p>
<br />

<p> 4.) <strong>Ping www.google.com - </strong>Within the Command Prompt, press ctrl + c to end the perpetual ping command. Within Wireshark click the green refresh button to clear the window (if prompted, don't worry about saving anything). This time, in Command Prompt, type "ping google.com" and observe the network traffic within both Wireshark and Command Prompt. Notice that the ping command is working (issuing requests and receiving replies). This indicates that the machine does in fact have internet connectivity.
</p>
<p>
<img src="https://i.imgur.com/9ulKmq8.png" />
</p>
<p>---------------------------------------------------------------------------------------------------------------------------------</p>
<br />

<p> 5.) <strong>Create a Security Rule for the Linux vm in Azure - </strong>It is very likely that the reason the Linux vm was not replying to the ping requests from the Windows vm was because there is a Security Rule in place that blocked ping requests (or no rule that allowed ping requests). Within Azure: navigate to the Linux vm -> Networking. Notice how there is a called "DenyAllInbound". For security purposes, this is a good rule to have in place on a fresh vm. However, we must enable ICMP traffic in order to ping this machine from the Windows vm. Click Add inbound port rule -> click the ICMP radio button -> Allow -> set Priority to 100 -> Add (Azure uses a hierarchy to apply inbound and outbound port rules where lower numbered rules take precedence). Once the rule is created successfully, attempt to ping the Linux machine with the same command from step 3. 
</p>
<p>
<img src="" />
</p>
<p>
<img src="" />
</p>
<p>---------------------------------------------------------------------------------------------------------------------------------</p>
<br />

<p> <strong></strong>
</p>
<p>
<img src="" />
</p>
<p>---------------------------------------------------------------------------------------------------------------------------------</p>
<br />
