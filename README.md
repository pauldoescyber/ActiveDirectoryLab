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
 <br />
 <br />
 <ol>
  <li>Open virtual box and name your Domain controller DC or domain_controller it really doesn't matter.Also while in this window ensure the version portion is selected as Other Windows
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/fa3a56dd-a3df-4910-afd2-c96a42fddc7d" height ="80%" width ="90%" alt ="Naming your domain controller">
  </li>
  <br/>
  <br />
   <li>Next is RAM allocation here it depends on your device.. considering later on in this project we will need to have both your DC and Client runnig I would suggest being conservative 
    with your RAM however for  the most part we alternate between the virtual machines so for me with 8GB of ram I decied to allocate 2GB 
of RAM to my windows server.
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/6fd66870-a7df-48b9-b3d6-74cc2d5cf732" height ="80%" width ="90%" alt ="RAM ALLOCATION">
  </li>
  <br />
  <br />
  <li>Click on continue for the reminder of the options , do not change anything yet until you create your vm,  your end result should be something like this.. shown below"
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/03669911-3842-4cb4-bf61-1e43eafbe1d1" height ="80%" width ="90%" alt ="Virtual machine created without an OS">
  </li>
  <br />
  <br />
   <li>Here we will go to Settings > General > Advanced and change the Shared Clipboard and drag and drop properties to bidrectional incase we want to copy something from our main 
    PC to our virtual machine."
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/5b763245-7c32-4626-b3a1-b2b0676ce69e" height ="80%" width ="90%" alt ="Changing shared clipboard and drag and drop to bidirectional">
  </li>
  <br />
  <br />
   <li>Next we will carry out processor allocation.Still depending on your computers capabilities you will assign a number of cores to your virtual machine
    for me I assigned 2 cores out my possible 8 which worked well for me. To do this go to Settings > System >  processor
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/08cb0e88-c10f-4635-8757-387a2e8faefa" height ="80%" width ="90%" alt ="Allocating the number of processors">
  </li>
  <br />
  <br />
 
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
