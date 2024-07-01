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
The first thing to do is download <a href="https://www.virtualbox.org/wiki/Downloads">virtual box</a> depending on the version of
 your OS <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/a38863c2-1a61-4622-b27f-33e61ae99d3f" height="80%" width="80%" alt="Downloading virtual box"/>
<br />
<br />
Next we will download <a href='https://www.microsoft.com/en-us/software-download/windows10ISO'>windows 10</a> ISO that will serve as the client... <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/27cc0f01-e95b-4758-b677-6fc7bd06477a" height="80%" width="80%" alt="Downloading Windows 10 ISO"/>
<br />
<br />
Next we will download <a href ="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">Windows server 2019 ISO </a>   <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/d8e2c9f0-d614-4bb3-b5d2-4224a37ad39f" height="80%" width="80%" alt="Downloading Windows server 2019"/>
<br />
<br />
The next step will be to set up our virtual machine using virtual box and  we will set up the Domain controller first:  <br/>
 This will include the following series of steps:
 <ol>
  <li>Open virtual box and name your Domain controller DC or domain_controller it really doesn't matter.Also while in this window ensure the version portion is selected as Other Windows
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/fa3a56dd-a3df-4910-afd2-c96a42fddc7d" height ="80%" width ="80% alt ="Naming your domain controller">
  </li>
   <li>On the version portion of this window ensure the version selcted is "Other Windows"
   <img src="" height ="80%" width ="80% alt ="Naming your domain controller">
  </li>
  <li>On the version portion of this window ensure the version selcted is "Other Windows"
   <img src="" height ="80%" width ="80% alt ="Naming your domain controller">
  </li>
  
 </ol>
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
