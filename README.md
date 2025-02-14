<h1>Creating an Active Directory and addings Users with Powershell</h1>


<h2>Description</h2>
This is used to build a working active direcotry which we will then add users utilzing powershell 
<br />

<h2>Prerequisites</h2>
- <b>Know how to use Virtualbox and be able to create new machines</b> 

<h2>Software Used</h2>

- <b>Virtualbox </b>
- <b>Powershell </b> 


<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Windows 2019 Server</b>

<h2>Downloads</h2>

-[Virtualbox](https://www.virtualbox.org/wiki/Downloads) <br/>
-[Windows 10 ISO](https://www.microsoft.com/en-us/software-download/windows10) <br/> 
-[Windows 2019 Server ISO](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019) <br/>


<h2>Setup Walk-through:</h2>

<p align="left">
Click the download link and download the correct pfsense version you need (AMD64 version works for most users) <br/> 
Select the DVD ISO Installer option: <br/>
<img src="https://i.imgur.com/iYxlJRu.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
In Virtualbox create a new machine and complete the following (once done click finish):  <br/>
Set Type to BSD <br/>
Set Version to FreeBSD(64-bit) <br/>
Allocate at least 2gb of Basse Memory <br/>
Allocate at least 19gb of virtual hard disk space <br/>
<img src="https://i.imgur.com/v7deaWG.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br />
<img src="https://i.imgur.com/JwEvz2n.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Select the machine and Click settings the click the network tab. Here we will be creating the network interfaces, adpater 1 will be our LAN, adpater 2 is our WAN, adapter 3 is our DMZ <br/>
For all adpaters make sure that "Enable Network Adaptor" is checked and do the following: <br/>
Adapter 1 Attached to is NAT <br/>
Adapter 2 Attached to is Internal Network <br/>
Adapter 1 Attached to is Internal Network <br/>
<img src="https://i.imgur.com/FKv6KgG.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<img src="https://i.imgur.com/1tYim7v.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Start the Virtual Machine and start the installation <br/>
<img src="https://i.imgur.com/BmDRGKu.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Choose all the default options and make sure you select the checkbox for the ZFS Configuration section:  <br/>
<img src="https://i.imgur.com/VZVpugG.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Select Yes for the next option and wait until installation is complete, once you get the complete box you must unmount the ISO or it will cycle through the boot process again:  <br/>
At the top bar of the Virtualbox go to Devices -> Optical Drives -> select your pfsense ISO -> Click Force Unmount <br/>
Click Reboot <br/>
<img src="https://i.imgur.com/io57SG0.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Create and install another virtual machine for Linux or Windows whichever you prefer (I used Linux)  <br/>
Edit the adapter 1 to be Attached to Internal Network and launch the new VM <br/>
Open the command line and type ifconfig (linux) or ipconfig (windows) <br/>
Check to see that the inet ip matches your LAN ip thats on PFsense 
<img src="https://i.imgur.com/9rRPKPU.png" height="80%" width="80%" alt="Firewall Steps"/>
<br/>
<img src="https://i.imgur.com/GA4Rpbg.png" height="80%" width="80%" alt="Firewall Steps"/>
<br/>
<br/>
You can try to ping the LAN ip in the command line to see if you get a response back <br/>
<img src="https://i.imgur.com/u3qFSN0.png" height="80%" width="80%" alt="Firewall Steps"/>
<br/>
<br/>
Open a web browser and type in the LAN ip, you will get a warning since there is no certificate, you can just ignore that an advance <br/>
<img src="https://i.imgur.com/AP54rb3.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br/>
<br/>
Login using the default credentials all lowercase for the username and password: <br/> 
Username is admin <br/>
Password is pfsense <br/>
<img src="https://i.imgur.com/nhHiR0V.png" height="80%" width="80%" alt="Firewall Steps"/>  
<br/>
<br/>
Go through the installation wizard and then you have your firewall all setup using pfsense!

  
</p>
