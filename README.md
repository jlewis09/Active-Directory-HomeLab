<h1>Active directory home lab</h1>

<h2>Description</h2>
In this project, I set up two VMs on VirtualBox: one for the Windows server that will host Active Directory and a Windows 10 ISO for the client. 
I then created and configured two network adaptors, one for the outside internet and one for the internal VM network.
I later configured RAS/NAT to allow the client on the private network to reach the internet through the domain controller.
also, DHCP was set up and configured on the domain controller to allow the created Windows 10 machine to automatically get an IP address.
Lastly, I created a PowerShell script to automatically create 1k users. 

<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 

<h2>Environments Used </h2>

- <b>Windows 10</b> 
- <b>Virtual Box</b>

<h2>Program walk-through:</h2>

<p align="center">
project Diagram: <br/>
<img src="https://i.ibb.co/3zkhstX/Active-directory.jpg" alt="Active-directory" height="80%" width="80%">
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
