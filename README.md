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
Virtual Machines:  <br/>
<img src="https://i.ibb.co/Np4K9YB/Virtual-machines.jpg" height="80%" width="80%" alt="virtual Machine"/>
<br />
<br />
External & Internal NIC: <br/>
<img src="https://i.ibb.co/jHy7rJx/External-Internal-NICs.jpg" height="80%" width="80%" alt="Network"/>
<br />
<br />
Static IP:  <br/>
<img src="https://i.ibb.co/YyN3Nnb/static-ip.jpg" height="80%" width="80%" alt="IP"/>
<br />
<br />
DHCP Scope:  <br/>
<img src="https://i.ibb.co/cJ3stvx/DHCP-Scope.jpg" height="80%" width="80%" alt="DHCP"/>
<br />
<br />
Powershell Scipt <br/>
 $PASSWORD_FOR_USERS   = "Password1"
$USER_FIRST_LAST_LIST = Get-Content .\names.txt
# ------------------------------------------------------ #

$password = ConvertTo-SecureString $PASSWORD_FOR_USERS -AsPlainText -Force
New-ADOrganizationalUnit -Name _USERS -ProtectedFromAccidentalDeletion $false

foreach ($n in $USER_FIRST_LAST_LIST) {
    $first = $n.Split(" ")[0].ToLower()
    $last = $n.Split(" ")[1].ToLower()
    $username = "$($first.Substring(0,1))$($last)".ToLower()
    Write-Host "Creating user: $($username)" -BackgroundColor Black -ForegroundColor Cyan
    
    New-AdUser -AccountPassword $password `
               -GivenName $first `
               -Surname $last `
               -DisplayName $username `
               -Name $username `
               -EmployeeID $username `
               -PasswordNeverExpires $true `
               -Path "ou=_USERS,$(([ADSI]`"").distinguishedName)" `
               -Enabled $true
}
<br />
<br />

Active Directory:  <br/>
<img src="https://i.ibb.co/BzM0rJV/ADD.jpg" height="80%" width="80%" alt="ADD"/>
<br />
<br />
1k+ Users list:  <br/>
<img src="https://i.ibb.co/HG0skwS/Users.jpg" height="80%" width="80%" alt="Users"/>
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
