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
<h2>Windows Server Setup</h2>
Click the download link and download the Windows 10 ISO and Windows Server ISO <br/> 
Lets start by creating the Windows Server which will be our Domain Controller, in Virtualbox complete the following: <br/>
1. Click New to create new machine <br/>
2. Name the machine something along the lines of DomainController or DC <br/>
3. Select ISO image and set version to "Other Windows(64-bit)" <br/>
4. Check the box that says "Skip unattended installation" <br/>
5. Set the memory size to at least 2gb (2048mb) <br/>
6. Click "Finish" <br/>
<img src="https://i.imgur.com/ZaG6frf.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Select the machine you made and click on settings <br/>
Go to the network tab <br/>
For adpater 1 select "attached to:" and choose NAT <br/>
Select adapter 2 and click the box taht says "Enable Network Adapter" <br/>
Select "attached to:" and choose Internal <br/>
<img src="https://i.imgur.com/CTg6lgB.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br />
<br />
Start the machine to begin the installation <br/>
Once a window pops up click next and then "Install Now" <br/>
Select the "Windows Server 2019 Standard Evaluation (Desktop Experience)" <br/>
Keep going through until it asks which type of installation you want, select "Custom" then Next <br/>
The installation will take some time <br/>
Once you get to customize settings, enter any password that is simple and you'll remember and click finish <br/>
<img src="https://i.imgur.com/n1qQBhv.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br />
<br />
Now to unlock the machine requires a special input that virtual machines dont allow <br/>
So on the top of the machine click on "Input" and then click Keyboard and select "Insert Ctrl+Alt+Del" <br/>
Enter the password you made earlier <br/>

<h2>Optional: Guest additions installation</h2>
This section is to install guesst additions which will help to scale your vm window size and help it run smoother but you can skip this <br/>
<br/>
On the top of your machine click on "devices" and select "Insert guest additions CD image"
Go to File explorer (Click the folder icon on the bottom) 
Click on "This PC" and select virtual box guest additions 
<img src="https://i.imgur.com/4JwmdG8.png" height="80%" width="80%" alt="Firewall Steps"/>  
<br />
<br />
Click on the "VBoxWindowsAdditions-amd64" and click through all the default options <br/>
Click on the "I want to manually reboot later" option <br/>
Shut the VM down by right clicking on the power button and selecting shutdown <br/>
<img src="https://i.imgur.com/vLerNjf.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br />
<br />
Start the machine and login again, and you should be all done with the optional guest installations! <br/>

<h2>Windows Server Setup part 2</h2>
At the bottom right of the machine click on the network icon (looks like a small computer) then click network <br/>
Click "Change adapter options" <br/> 
<img src="https://i.imgur.com/F1SNBdZ.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br />
<br />
Here we will have to figure out which of the 2 network connections is the internet and which is the internal network <br/>
Right click on one of the connections and select "Status" then click "Details" <br/>
In the IPv4 section if you see an ip along the lines of 10.0.0.1 or anything starting with 10 this is most likley your home internet <br/>
<br/>

<p align="Center">
Home Internet Connection <br/>
<img src="https://i.imgur.com/ChwzdEh.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Internal Network Connection
<img src="https://i.imgur.com/oN0Za4O.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />

<p align="Left">
Right click on your Home Internet connection and select "rename" <br/>
Rename it to something like "internet" or "homeInternet" <br/>
Right click on your Internal Network connection and select "rename" <br/>
Rename it to something like "Internal" or "X_Internal_X" <br/>
<img src="https://i.imgur.com/cTjFVVJ.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Right click on your internal network and select "Properties" <br/>
Double click on the option "Internet Protocol Version 4 (TCP/IP)" <br/>
Make sure what you enter matches exactly as the following image <br/>
<img src="https://i.imgur.com/M41QkW1.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Click "Ok" to finish <br/>
Now we're going to rename our PC, right click on the windows icon in the bottom left <br/>
Click "System" <br/>
Click "Rename this PC" and name it something like "DomainController" or "DC" <br/>
Click "Next" then "Restart Now" <br/>
<img src="https://i.imgur.com/piM21Yi.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Now we're going to install Active Directory domain services <br/>
Log back into your machine and on the server manager page that appears click on "Add roles and features" <br/>
Keep selecting the default values for each section until you get to the "server role" section <br/>
Select "Active Directory Domain Services" then click add features on the new popup <br/>
Then keep clicking next until you are able to click install and wait for the installation <br/>
<img src="https://i.imgur.com/9q6kJAc.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
On the top Server manager dashboard there should be a flag icon witha yellow warning symbol <br/>
Click on it and click "Promote this server to a domain controller" <br/>
<img src="https://i.imgur.com/9wa1U9J.png" height="80%" width="80%" alt="Firewall Steps"/> 
<br />
<br />
Select "Add a new forest" <br/>
Name the domain anything you want (example: mydomain.com) <br/>
<img src="https://i.imgur.com/arxLoSX.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Click Next <br/>
Enter any password you'll remember <br/>
Keep clicking next until you are able to install, then install <br/>
Log back in to the machine and click on the windows start icon in the bottom left <br/>
Click on "Windows Adminstrative tools" <br/>
Click on "Active Directory User and Computers"  <br/>
<img src="https://i.imgur.com/nfk4oab.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Righ click on the domain name you made (Ex: mydomain.com) then select "New" and click on "Organizational Unit" <br/>
Name the folder "_ADMINS" and uncheck the box below it <br/>
<img src="https://i.imgur.com/FIJX7Aj.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Right click on the new "_ADMINS" folder and select "New" <br/>
Click "User" <br/>
Fill in your name for First name and last name sections <br/>
In "User logon name" put a- and then your first initial with your last name (EX: a-rrivera) <br/>
<img src="https://i.imgur.com/BgFLpXw.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Click Next <br/>
Enter a password you will remember <br/>
Make sure the only thing that is checked is "Password Never Expires"  <br/>
<img src="https://i.imgur.com/Cy2z2WW.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Click Next and Finish <br/>
You will see the new User created, right click on it and select "Properties" <br/>
Select the "Member of" tab <br/>
Click on "Add" <br/>
Type in "domain admins" and click "Check Names" which should resolve the name you entered  <br/>
<img src="https://i.imgur.com/h3yFmj3.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Click Ok and then click "Apply" <br/>
Right click on the windows icon in the bottom left and click Sign Out <br/>
Select "Other User" <br/>
To login use the account you created earlier (EX: a-rrivera)  <br/>
<img src="https://i.imgur.com/YhPzbSq.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Now we will install Ras/NAT <br/>
On the Server manager dashboard click on "Add roles and features" <br/>
Click next until you get to the "Server Roles" section <br/>
Select "Remote Access" and click next until you get to the "Role Services" section <br/>
Select "Routing" and click "Add Features" <br/>
Click Next until you get to install and begin the installation <br/>
<br />
<br />
On the Server Manager dashboard, on the top right click on "Tools" and select "Routing and remote Access" <br/>
Right click on where it says your pc name (local) (EX: DC (local)) and select "Configure and Enable Routing and Remote Access" <br/>
Click Next and select NAT <br/>
Select the Home Internet interface you named (Note: if nothing appears in the table then click cancel and navigate back to the section and it should appear this time) <br/>
Then Click Next and Finish <br/>
<img src="https://i.imgur.com/2JJvCMH.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Your PC Name (local) should now have a green arrow on it to indicate it was successful <br/>
Now we will setup a DHCP server for new users for our WIndows 10 client <br/>
On the Server manager dashboard click on "Add roles and features" <br/>
Click next until you get to the "Server Roles" section <br/>
Select "DHCP Server" and click "Add Features" <br/>
Finish and install <br/>
<br />
<br />
On the Server Manager dashboard, on the top right click on "Tools" and select "DHCP" <br/>
On the left side of the table click on your domain dropdown (EX: dc.mydomain.com) <br/>
<img src="https://i.imgur.com/3xfy1kB.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Right click on IPv4 and select "New Scope" <br/>
You can name it whatever you want but I'll name it after the ip range (EX: 172.16.0.100-200) <br/>
Click next and make sure what you enter exactly macthes the following screen shot <br/>
<img src="https://i.imgur.com/67j0re1.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />
Keep the defaults for each section until you get to "Router (Default Gateway)" <br/>
Here you will enter the ip 172.16.0.1 and click "Add" <br/>
Click through everything else until you click finish  <br/>
<br />
<br />
Right click on your domain name (EX: dc.mydomain.com) and select "Authorize" <br/>
Right click it again and select "Refresh" <br/>
Green arrows should appear on the IPv4 and IPv6 icons <br/>
<img src="https://i.imgur.com/EkgPEs5.png" height="80%" width="80%" alt="Firewall Steps"/>
<br />
<br />




















  














  
</p>
