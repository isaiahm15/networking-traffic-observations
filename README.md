<br><h1 align="center">Traffic Observation Exercise</br>
<br>
<img src="https://cdn-icons-png.freepik.com/256/11276/11276084.png?semt=ais_white_label" height="200" width="200"/></br>
</h1>
This guide will show you how to observe different traffic traveling between two hosts in a network. We'll being using two preconfigured VMs from Azure: one Windows 10 client, and a Linux Ubuntu server, both of which are connected to the same virtual network.
<br/>


<h2>Databases & Programs Used</h2>
<p>
 
- <b>Powershell</b>

- <b>[Wireshark](https://www.wireshark.org/download.html)</b>

</p>

<h2>Environments Used</h2>
<p>
 
- <b>Windows 10 Enterprise</b> (22H2)
- <b>Ubuntu Server 22.04 LTS</b> (x64 Gen2)
- <b>Azure</b>

</p>

<h2 align="center">Installing Wireshark</h2>

<p>Download Wireshark for Windows from their website.
<br><img src="https://github.com/user-attachments/assets/279512fe-cd26-4a4c-a6e3-408b87991833" height="75%" width="100%"/>
<br/>
</p>

<p>Launch the Wireshark installer after downloading and proceed to install.
<br><img src="https://github.com/user-attachments/assets/4e122243-570e-483a-9014-1f1bf4c0b17a" height="75%" width="100%"/>
<br/>
</p>

<p>Open the Wireshark application. From here, you can double-click on "Ethernet" and begin observing traffic in your network.
<br><img src="https://github.com/user-attachments/assets/09494a1b-00db-4c06-b70d-b1f2a0c926f2" height="75%" width="100%"/><img src="https://github.com/user-attachments/assets/bb5f4e38-6d6d-4ba9-ab50-ba04a71a572a" height="75%" width="100%"/>
<br/>
</p>

<h2 align="center">DHCP Traffic</h2>

<p>Create a .txt file on your Windows 10 client and add both the <strong>ipconfig /release</strong> and <strong>ipconfig /renew</strong> commands in it. Click on File > Save As and save the .txt file as a .bat file instead.
<br><img src="https://github.com/user-attachments/assets/a3432bff-bb17-4bbc-9e0b-49674749e5eb" height="75%" width="100%"/>
<br/>
</p>

<p>To run the .bat file in Powershell, you'll need the path directory for the .bat file. Once this file successfully runs, you'll be able to view just the network traffic for the release/renew process by searching "DHCP" in Wireshark.
<br><img src="https://github.com/user-attachments/assets/cc3072dc-cf99-4905-99b4-fd79e5ded60a" height="75%" width="100%"/>
<br/>
</p>

<h2 align="center">DNS Traffic</h2>

<p>Use <strong>nslookup</strong> and search for a domain name.
<br><img src="https://github.com/user-attachments/assets/1386a31c-aeab-45f2-843d-3f2de5def2a2" height="75%" width="100%"/>
<br/>
</p>

<p>Then, you can view DNS traffic from the previous command in Wireshark by searching "DNS".
<br><img src="https://github.com/user-attachments/assets/8414fa00-ad8b-418c-a255-2d7939579696" height="75%" width="100%"/>
<br/>
</p>

<h2 align="center">ICMP Traffic</h2>

<p>Ping your Linux VM's private IP address from the Windows 10 client. Search for "ICMP" in Wireshark's capture search bar to observe only ICMP network traffic, where you should see request and reply pings between the two hosts on the virtual network.
<br><img src="https://github.com/user-attachments/assets/f942db6f-d664-47da-bcf5-f7016dfe0933" height="75%" width="100%"/></br>
<br><img src="https://github.com/user-attachments/assets/c4ffc4d8-0a8a-4a47-85a0-6f21f1621a19" height="75%" width="100%"/>
<br/>
</p>

<h2 align="center">RDP Traffic</h2>

<p>Since we're remoted into a virtual machine, remote network traffic is already active and doesn't require Powershell. Simply search <strong>tcp.port == 3389</strong> to view all RDP network traffic.
<br><img src="https://github.com/user-attachments/assets/79721d38-62ce-4e9a-a8e0-beda34d0f738" height="75%" width="100%"/>
<br/>
</p>

<h2 align="center">SSH Traffic</h2>

<p>First, you'll have to log into your Linux server from Powershell in your Windows 10 client. Use <strong>ssh "(your linux user login name)@(your linux VM's private IP address)</strong>" and press enter. From here, you can type yes to successfully connect.
<br><img src="https://github.com/user-attachments/assets/d884e425-3b63-4136-8481-6827e4874953" height="75%" width="100%"/>
<br/>
</p>

<p>Use some commands like <b>pwd</b>, <b>uname</b> or <b>uname -a</b>, and then use <b>exit</b> to close the Linux server connection.
<br><img src="https://github.com/user-attachments/assets/167009b3-9af2-4504-b1a8-36dd866ff440" height="75%" width="100%"/>
<br/>
</p>

<p>You'll be able to observe the prior Linux server activity through Wireshark by searching "SSH".
<br><img src="https://github.com/user-attachments/assets/b281ca39-64d9-486a-bc7c-e8191f5a315d" height="75%" width="100%"/>
<br/>
</p>

That's it! Knowing how to view specific network traffic will allow you to break through the noise of a busy network for intricate troubleshooting.
