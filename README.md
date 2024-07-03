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
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/a90d966f-e879-441a-aa42-50636e0eb665"
" height="80%" width="80%" alt="ADlab project overview"/>
<br />
<br />
The first thing to do is download <a href="https://www.virtualbox.org/wiki/Downloads">virtual box</a> depending on the version of
 your OS <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/ac28e79d-b991-48b2-a4f5-41fe060cc252" height="80%" width="80%" alt="Downloading virtual box"/>
<br />
<br />
Next we will download <a href='https://www.microsoft.com/en-us/software-download/windows10ISO'>windows 10</a> ISO that will serve as the client... <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c0dc0220-945b-489b-b490-94c3dca9ad61"
 height="80%" width="80%" alt="Downloading Windows 10 ISO"/>
<br />
<br />
Next we will download <a href ="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">Windows server 2019 ISO </a>   <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/1e6a9319-74ac-4a84-8076-e31fdd23b719" height="80%" width="80%" alt="Downloading Windows server 2019"/>
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
of RAM to my DC.
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/6fd66870-a7df-48b9-b3d6-74cc2d5cf732" height ="80%" width ="90%" alt ="RAM ALLOCATION">
  </li>
  <br />
  <br />
  <li>Click on continue for the reminder of the options , do not change anything yet until you create your vm,  your end result should be something like this.. shown below"
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/03669911-3842-4cb4-bf61-1e43eafbe1d1" height ="80%" width ="90%" alt ="Virtual machine created without an OS">
  </li>
  <br />
  <br />
   <li>Next we will go to Settings > General > Advanced and change the Shared Clipboard and drag and drop properties to bidrectional incase we want to copy something from our main 
    PC to our virtual machine."
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/5b763245-7c32-4626-b3a1-b2b0676ce69e" height ="80%" width ="90%" alt ="Changing shared clipboard and drag and drop to bidirectional">
  </li>
  <br />
  <br />
   <li>
    Next we will carry out processor allocation,depending on your computer's capabilities you will assign a number of cores to your virtual machine
    for me I assigned 2 cores out of a  possible 8 which worked well for me.To do this go to Settings > System > Processor
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/08cb0e88-c10f-4635-8757-387a2e8faefa" height ="80%" width ="90%" alt="Allocating the number of processors">
  </li>
  <br />
  <br />
   <li>Next we will set our DC to have two NICS,one for external conncectivty and one  for the internal domain members.We do this by going to Settings >
    Network once here we will find one adapter(under adapter 1) and it will be for NAT purposes, this will be the NIC used for an external conncection    to        the internet. We will select adapter 2 to add an extra NIC (adapter 2) we do this by checking the enable adapter box, and the purpose for the second NIC should be internal Network as illustrated the figure below
   
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c726d180-65d8-4a55-810f-d7a52aaec680" height ="80%" width ="90%" alt ="Allocating the number of processors">
  </li>
  <br />
  <br />
   <li>Next we will set start our Domain controller/DC (either by double clicking the machine or the power button next to it) and upon starting it, it will
    basically prompt us for an Operating System as our machine is on but we haven't given it an OS yet so what we will do is we will click on the 
    small icon denoting folders and navigate to where we stored our Server 19 ISO(that we downloaded earlier) and it will probably be saved under a different name
    and we will select it and have it as our disk image, and finallly we will press start.As shown in the series of images below.
   
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/fcdaf33d-0689-4484-a908-30cd42d1f510" height ="80%" width ="90%" alt ="Clicking on Icon folder">
   <br />
   <br />
 <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/05c4adc2-f5e1-436c-9bc8-80b4e32595a8" height ="80%" width ="90%" alt ="Clicking on the add button to navigate to the downloaded ISO">
   <br />
    <br />
     <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/718989d9-c010-46f3-aa9a-6fe9780f1646" height ="80%" width ="90%" alt ="Selecting your server 19 ISO">
   <br />
    <br />
    <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/9cc880a7-1b38-4c43-bcfb-4c3f963e9e91" height ="80%" width ="90%" alt ="Final stage in selecting ISO for your pc">
   <br />
    <br />
  </li>
    <li>Next will be setting up the server and initial configurations, the first thing to note is the OS to pick should be Window's Server Standard Evolution 2019(Desktop Experience)
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/900f03a4-7411-40d6-8b76-7abc8ca3b64b" height ="80%" width ="90%" alt ="Clicking on Icon folder">
    </li>
  <br />
  <br />
   <li>Click on Next until you arrive at the window where you will be prompted for a pasword in the intial login and here place the password as  "Password1" for all passwords in the lab.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/2a468d90-a5e9-476a-8282-338fdf40699e" height ="80%" width ="90%" alt ="Clicking on Icon folder">
    </li>
  <br />
  <br />
   <li>Once you set the password to unlock your server you need to input control alt delete.However this won't be possible from your host machine, hence the way to do this is input>keyboard>insert control+alt+delete as shown below
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/a5c4e016-6a17-4dda-8b8c-5b2beba5204d" height ="80%" width ="90%" alt ="Entering your virual machine">
    </li>
  <br />
  <br />
   <li>The next step would be to install Virtual Box guest CD additions to make your user experience smooth,while you use the vm. To do this click on devices followed by insert Guest additions CD image.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/924f759b-6a53-4e40-83b5-91435786b2bf" height ="80%" width ="90%" alt ="Installing Guest additions CD image">
    </li>
  <br />
  <br />
   <li>Once the additonal cd image has finished runnig opt to manually reboot later. THis is because the restart now option did not effect the desired results.This is illustrated bellow.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/1ecb376f-b98b-469e-9a4d-b4941f2b47d1" height ="80%" width ="90%" alt ="Entering your virual machine">
    </li>
  <br />
  <br />
  <li>The next step will be to rename the two NICS on the virtual machine, first by identifying which NIC was responsible for what.
    To navigate to this we will click on the ethernet icon at right side of the task bar. Next click on network and then change adapter options.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/19e342ad-c8fd-4f1f-8135-c2040b375fa4" height ="80%" width ="90%" alt ="Entering your virual machine">
    </li>
  <br />
  <br />
   <li>The next step is to identify between the two NICS which one is for the internal network and which one is for the external network.How we will do this is by right clicking on one of the  NICS and then selecting status and then details then observing the addressing information. If the IP addreess
    on the NIC starts with 10.0. (most probably be 10.0.2.15) this would indicate the NIC is external and for connectivity to the internet. Right click on the said NIC and rename it to _INTERNET_ for ease of identification and future use. THis has been illustrated below.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/f4bafe8b-5216-4ebd-89dd-c9a8b60c29bd" height ="80%" width ="90%" alt ="Renaming the NICS based on functionality">
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
+ text in green![Unlocking your vm](https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/cd882f28-f88d-4ae2-8cee-943449d249e3)

! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
