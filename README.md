<h1>Active Directory Lab set up</h1>


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
   <li>Click on Next until you arrive at the window where you will be prompted for a pasword in the intial login and here place the password as  "Password1"(Do this for all the passwords in the lab.)
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
  <li>Double click and run Virtual box Guest additions.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/07a2d90b-6f58-4b0d-9bb3-0d47ef31ca6d" height ="80%" width ="90%" alt ="Checking reboot manually option after CD image is installed">
    </li>
  <br />
  <br />
   <li>Once the additonal cd image has finished runnig opt to manually reboot later. THis is because the restart now option did not effect the desired results.This is illustrated bellow.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/1ecb376f-b98b-469e-9a4d-b4941f2b47d1" height ="80%" width ="90%" alt ="Checking reboot manually option after CD image is installed">
    </li>
  <br />
  <br />
  <li>The next step will be to rename the two NICS on the virtual machine, first by identifying which NIC was responsible for what.
    To navigate to this we will click on the ethernet icon at right side of the task bar. Next click on network and then change adapter options.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/19e342ad-c8fd-4f1f-8135-c2040b375fa4" height ="80%" width ="90%" alt ="Navigating to NICS">
    </li>
  <br />
  <br />
   <li>The next step is to identify between the two NICS which one is for the internal network and which one is for the external network.How we will do this is by right clicking on one of the  NICS and then selecting status and then details then observing the addressing information. If the IP addreess
    on the NIC starts with 10.0. (most probably be 10.0.2.15) this would indicate the NIC is external and for connectivity to the internet. Right click on the said NIC and rename it to _INTERNET_ for ease of identification and future use. THis has been illustrated below.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/037f6dda-d613-41c5-8b1f-938c2d7fc9f4" height ="80%" width ="90%" alt ="Renaming the EXTERNAL NIC">
    </li>
  <br />
  <br />
     <li>The next step will be to rename the second NIC to x_internal(it can be anyname you so choose ..) to confirm it is the internal NIC when you inspect its IP address you should find an IP of 169.254.196.74 or something like that which would denote that the NIC
      was looking for a DHCP server and was unable to get one.Just to confirm you have the right NIC.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/e690bd49-c4cb-4e33-93d1d8270673dd21" height ="80%" width ="90%" alt ="Renaming the INTERNAL NIC">
    </li>
  <br />
  <br />
     <li>The next step will be to rename the PC, Right click start Menu > System > Click rename this PC(Easiest way to do this you can still go the longer route via settings and about).We can opt to name this "DC"(for domain controller) click Next and Click Restart Now.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c8360b5d-fdc2-47f9-9b6b-3f2abb0d0078" height ="80%" width ="90%" alt ="Renaming PC">
    </li>
  <br />
  <br />
      <li>The next step will be assign an IP address to our internal NIC as well as our DNS server.We will click on the ethernet ICON on the taskbar on the bottom and navigate to our two NICS(by clicking on change adapter options).Follow the steps in the image
       below from step one through six.
        <video  height = "80%" width ="90%" controls> <source="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/898a0ce2-1137-4689-b106-9efb5dbba035" type ="video/mp4"> </video>
    </li>
  <br />
  <br />
  <li>The next step will be to install Active Directory domain services (AD DS) and then create a domain.On the server manager , 1.click add roles and features, 2.click on next until when asked which server you would like to install the feature on and as you have only one server click on it and select next as illustrated. 3.Click on next and check the Active Directory Domain services box 4.Click Next until you arrive at the installing page and then click install. The successful installation page has been demonstrated as well
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/671ff7eb-b7c3-4689-bcd1-42e548078e67" height ="80%" width ="90%" alt ="Adding
         roles and features">
   <br />
    <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/8ec87a9e-aec9-4897-8ff7-0af817bf5eaa" height ="80%" width ="90%" alt ="Selecting
     the server to install it on.">
   <br />
    <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/83314597-4931-4b97-9e23-ddbbedcc8033" height ="80%" width ="90%" alt ="Checking the AD DS box.">
   <br />
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/0124e4c9-f283-4e1f-92d7-283455b59498" height ="80%" width ="90%" alt ="Successful AD DS installation role.">
    </li>
  <br />
  <br />
   <li>Still on your windows server manager you will notice a yellow caution sign on the flag. As demonstrated below, this flag  shows that we installed the softwate but we did not actually create/configure our domain and hence this needs to be done as well.The flag is shown on the figure below
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/bfe158d1-c07c-418e-9e5b-9766947af6cc" height ="80%" width ="90%" alt ="Flag denoting lack of postdeployment configuration">
    </li>
  <br />
  <br />
   <li>The next step will be post deployment configuration, here we will actually create the domain via the following steps: 1. Click the yellow caution sign and select promote this server to a doman controller. 2. Add new forest 3. Name the domain mydomain.com(can be named anything in reality but just for the sake of the lab we shall name it mydomain.com) 4. Click on Next, when asked for a Password enter "Password 1" as we discussed earlier all passwords in the lab to be password 1. 5. Click on next until the Installation point, When it finishes intalling it will automatically restart the computer for us.
    </li>
  <br />
  <br />
  <li>Once the virtual machine has restarted you will notice the login page is different as show below.This would mean the previous step was conducted successfully. i.e successful configuration of AS DS. Login with the password Password1 or the password you had precviously placed
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c2802d87-c20f-4df9-a7c9-4b0eae498794" height ="80%" width ="90%" alt ="AD-DS configured successfuly">
    </li>
  <br />
  <br />
  <li>The next step would be to create our own dedicated Admin domain account instead of using the built in Admin account. To do this we go to start Admin tools > Active directory Users and Computers. Right click mydomain.com and then New and then create Organizational Unit(An Organizational Unit in Active directory is a subdivision in AD which you can place other users, computers or other organizational units (its kind of like a directory). Name it _ADMINS and uncheck the container from accidental deletion(for convience reasons).Right click on the new OU you have just creates the _ADMINS then click on new and then user. Provide your first and last name, for the user name the best practice is a- followed by  initial of first name, followed by lastname(in full). Press next for the passoword section enter password one just for this lab.Uncheck user must change password in next login and check password never expires box.Click next and on finally click finish. The series of images below convey the following steps.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/e2b76986-2bbc-4017-930d-95c01f0f6eb1" height ="80%" width ="90%" alt ="Navigating to AD users and computers">
   <br />
   <br />
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/209981cd-5dfd-4f49-96d8-f81dfd9d899a" height ="80%" width ="90%" alt ="Navigating to Organizational Unit">
     <br />
    <br />
           <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/ee270203-f296-4b36-bf30-646120dfc437" height ="80%" width ="90%" alt ="Renaming the Organizational Unit _ADMINS">
     <br />
    <br />
         <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/1af27652-7cf5-44ec-b843-865bad93558d" height ="80%" width ="90%" alt ="Creating a new user">
     <br />
    <br />
         <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/49e823c4-aef8-4d6c-adaf-e092cc21150b" height ="80%" width ="90%" alt ="Naming the Admin">
     <br />
    <br />
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/f1fe8db2-ff64-4783-a4d2-a47844108989" height ="80%" width ="90%" alt ="Creating Password for the Admin">
     <br />
    <br />
   
   </li>
  <br />
  <br />
    <li>Once we complete the steps above we will have an account however our account will not be an adminstrator account, we need to take do the following to make the account we have just created an admin account.Right click the account we have just created and go to properties.Click  member of, and then click add, and then under the space for enter object names write domain admins and click check. It should resolve to domain admins, click ok, and finally click apply.In my example because I have done it before it does tell me that I can't add it twice but it should work fine for you.
     <br />
     
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/ae6547e9-1e42-4df4-ba8d-88a0ac30142c" height="80%" width="90%" alt="Navigating to User properties"/>
    <br />
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/38a9632e-8a07-4cf7-9993-a6ee7fa15165" height="80%" width="90%" alt="Navigating to Member of"/>
   <br />
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/98a850e5-44a6-4d48-bc54-2023458aa807" height="80%" width="90%" alt="Finally creating the admin as user"/>
   <br />
   <br />
    </li>
  <br />
  <br />
   <li>To use the newly created admin account sign out of your server and instead of loging in into the my administrator page
    select other user as show below, and use the user name you had writted down when creating the account, for my lab it was
    "a-pisaac" and the password we had set for this which we have set for all things in this lab to be password1.
    <br />
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/dd6cb0ca-a2fa-4874-b4f4-4cc1e7bcf4d5" height ="80%" width ="90%" alt ="Singing in and singing out to gain acess to the new admin account">
    </li>
  <br />
  <br />
  <li>
   The next thing to do is to configure RAT/NAS (Remote Acess Server/Network Address translation) on your server to allow members of your domain to conncet to the interntet via the domain controller still whilst on the private network. We will go to (in server manager) add roles and features click on next a couple of times, select the current server. For roles select remote access. Click on next and check the box for routing. Click on next a couple of times then click install The series of images show the following processes.
   <br />
   <br />
   <img src ="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/fef584ba-4763-4a88-bcdb-3a42d74ba860" height ="80%" width ="90%" alt="Click on add roles">
   <br />
   <br />
     <img src ="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/79f76d79-63af-49ad-afb9-0891f2b5ade6" height ="80%" width ="90%" alt="selecting the current server">
   <br />
   <br />
     <img src ="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/058cf46e-edfb-4d9b-ae08-7bbea81d5ff2" height ="80%" width ="90%" alt="checking the RAS Box">
   <br />
   <br />
     <img src ="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/83028ec7-6dd2-446c-a928-5811d194aa7d" height ="80%" width ="90%" alt="Selecting the Routing option under role option">
   <br />
   <br />
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
+ text in green![Unlocking your vm](https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/cd882f28-f88d-4ae2-8cee-943449d249e3)

! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
