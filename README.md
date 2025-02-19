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
Click on the "VBoxWindowsAdditions-amd64" and click through all the default options
Click on the "I want to manually reboot later" option
Shut the VM down by right clicking on the power button and selecting shutdown 
<img src="https://i.imgur.com/vLerNjf.png" height="80%" width="80%" alt="Firewall Steps"/>  





  
</p>
