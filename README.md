<h1>Active Directory Lab set up</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
In this lab, I replicated a small office  network by using virtual machines (virtual box) to create a domain controller with two NICs (windows server 2019) and a client host on the network (Windows 10). On the domain controller I configured DNS, DHCP, AD DS and also made my own domain in which  a user could conncect and be a part of.The domain controller was used as the default gateway for devices in the domain.I also used a powershell script to generate users (about a thousand users) that would be part of the domain using powershell.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Virtual Box</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2) 

- <b>Windows server 2019 </b>

<h2>PROJECT OVERVIEW:</h2>

<p align="center">
Project overview: <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/2b73d24d-2ec7-4fab-99d7-941bb4bb33d7" height="80%" width="80%" alt="ADlab project overview"/>
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