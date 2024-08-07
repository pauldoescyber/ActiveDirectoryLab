<h1>Active Directory Lab set up</h1>


<h2>Description</h2>
In this lab, I replicated an office enviroment by using virtual machines (virtual box) to create a domain controller with two NICs (windows server 2019) and a client host on the network (Windows 10). On the domain controller I configured DNS, DHCP, AD DS and also made my own domain in which  a user could conncect and be a part of.The domain controller was used as the default gateway for devices in the domain.I also used a powershell script to generate users (about a thousand users) that would be part of the domain using powershell.
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
<img src="https://github.com/user-attachments/assets/3770756c-5856-441a-b461-2147c82433c7" height="100%" width="100%" alt="ADlab project overview"/>
<br />
<br />
 
 # Downloading the enviroment
The first thing I did is to download <a href="https://www.virtualbox.org/wiki/Downloads">virtual box.</a> <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/ac28e79d-b991-48b2-a4f5-41fe060cc252" height="80%" width="80%" alt="Downloading virtual box"/>
<br />
<br />

 # Downloading the Operating Systems.
 I downloaded the  <a href='https://www.microsoft.com/en-us/software-download/windows10ISO'>windows 10</a> ISO that will serve as the client. <br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c0dc0220-945b-489b-b490-94c3dca9ad61"
 height="80%" width="80%" alt="Downloading Windows 10 ISO"/>
<br />
<br />
Next I downloaded the  <a href ="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">Windows server 2019 ISO </a> that will serve as the Domain controller.<br/>
<img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/1e6a9319-74ac-4a84-8076-e31fdd23b719" height="80%" width="80%" alt="Downloading Windows server 2019"/>
<br />
<br />

# Setting up the virtual machine.
Next I set up my virtual machine using virtual box and I set up the Domain controller first:  <br/>
 This included the following series of steps:
 <br />
 <br />

  <li>Inside virtual box I clicked on the the new button.Next I named my Domain controller DC or domain_controller it really doesn't matter.Also while in this window I ensured the version portion is selected as Other Windows
   <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/fa3a56dd-a3df-4910-afd2-c96a42fddc7d" height ="80%" width ="90%" alt ="Naming your domain controller">
  </li>
  <br/>
  <br />
   <li>Next is RAM allocation here it depends on your device.. considering at the nearly the  end of  this project we will need to have both your DC and Client runnig I would suggest being conservative 
    with your RAM however for  the most part we work on the Domain controller so for me with 8GB of ram I decied to allocate 2GB 
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

  # Renaming the two NICS
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

  # Renaming the PC
  <li>The next step will be to rename the PC, Right click start Menu > System > Click rename this PC(Easiest way to do this you can still go the longer route via settings and about).We can opt to name this "DC"(for domain controller) click Next and Click Restart Now.
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c8360b5d-fdc2-47f9-9b6b-3f2abb0d0078" height ="80%" width ="90%" alt ="Renaming PC">
    </li>
   
  <br />
  <br />
      <li>The next step will be assign an IP address to our internal NIC as well as our DNS server.We will click on the ethernet ICON on the taskbar on the bottom and navigate to our two NICS(by clicking on change adapter options).Follow the steps in the image below from step one through six.
      <img src="https://github.com/user-attachments/assets/27f90dfe-9dff-4de3-815e-92de1619faf5" height ="80%" width ="90%" alt ="IP addressing of NIC(0)">
      <br />
      <br />
            <img src="https://github.com/user-attachments/assets/13483bce-e587-4150-9d2a-6acae574244a" height ="80%" width ="90%" alt ="IP addressing of NIC(1)">
    </li>
  <br />
  <br />


  # Setting up Active Directory Domain Services (AD DS)
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
  
  # Post Deployment configuration of AD DS
   <li>Still on your windows server manager you will notice a yellow caution sign on the flag. As demonstrated below, this flag  shows that we installed the softwate but we did not actually create/configure our domain and hence this needs to be done as well.The flag is shown on the figure below
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/bfe158d1-c07c-418e-9e5b-9766947af6cc" height ="80%" width ="90%" alt ="Flag denoting lack of postdeployment configuration">
    </li>
  <br />
  <br />
   <li>The next step will be post deployment configuration, here we will actually create the domain via the following steps: 1. Click the yellow caution sign and select promote this server to a doman controller. 2. Add new forest 3. Name the domain mydomain.com(can be named anything in reality but just for the sake of the lab we shall name it mydomain.com) 4. Click on Next, when asked for a Password enter "Password 1" as we discussed earlier all passwords in the lab to be password 1. 5. Click on next until the Installation point, When it finishes intalling it will automatically restart the computer for us.The series of images highlight the key elements of this process.
      <img src="https://github.com/user-attachments/assets/eea6bf77-6eab-46cf-892a-3635e53f8826" height ="80%" width ="90%" alt ="Post-deployment-configuration(0)">
   <br />
   <br />
      <img src="https://github.com/user-attachments/assets/5cad45e4-3ad9-4177-b2d3-369fda0b5218" height ="80%" width ="90%" alt ="Post-deployment-configuration(1)">
   <br />
   <br />
<!--       <img src="https://github.com/user-attachments/assets/61ad36b0-258f-4038-b726-eeff7cc8ffde" height ="80%" width ="90%" alt ="Post-deployment-configuration(2)">
   <br />
   <br /> -->
      <img src="https://github.com/user-attachments/assets/d774a7f9-9de8-427b-9920-e7ffc854b11b" height ="80%" width ="90%" alt ="Post-deployment-configuration(3)">
   <br />
   <br />
      <img src="https://github.com/user-attachments/assets/0e0cc1c9-487b-4950-9a17-6a5c0e6fc120" height ="80%" width ="90%" alt ="Post-deployment-configuration(4)">
   <br />
   <br />
    </li>
  <br />
  <br />
  <li>Once the virtual machine has restarted you will notice the login page is different as show below.This would mean the previous step was conducted successfully. i.e successful configuration of AS DS. Login with the password Password1 or the password you had precviously placed
        <img src="https://github.com/pauldoescyber/ActiveDirectoryLab/assets/172483061/c2802d87-c20f-4df9-a7c9-4b0eae498794" height ="80%" width ="90%" alt ="AD-DS configured successfuly">
    </li>
  <br />
  <br />

  # Creating a dedicated Admin domain account
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
  
  # Configuring RAT/NAS
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
   <img src ="https://github.com/user-attachments/assets/d5ddd35b-f4cc-4ac5-8c07-fbbcc54524e9" height ="80%" width ="90%" alt="Complete-installation-RAT">
   <br />
   <br />
  </li>
  <li>
   Once this has been completed.On the Server Dashboard select tools > Routing and Remote Acess. If the DC local has a red dot on  the symbol do the following. Right click it and press configure and enable routing and remote access and it should open  a Routing and Remote Acess server setup wizard.Inside the setup wizard select next, and in the configuration options select NAT and click next. Under Nat internet connection you may not be able to access the first option(use this public interface to connect to the internet) to fix this cancel and leave the wizard setup and go through the above steps again until you reach the Nat internet connection option within the wizard.(Unsure why this occurs).Once you have done this select this
   option (use this public interface to connect to the internet) and make sure you select the nic that we had named for connecting to the internet.. for us its the INTERNET NIC then select the next option and finally select the Finish option.
   The series of images highlights the following above process.
   <br />
   <br />
   <img src="https://github.com/user-attachments/assets/7275e9bc-ca00-406c-a4fc-4d1fdaa8ab7a" height="80%" width="80%" alt="Routing and remote access(0)"/>
<br />
<br />
 <img src="https://github.com/user-attachments/assets/94b1bda7-0929-4b90-8dcb-0ebd49da3a87" height="80%" width="80%" alt="Routing and remote access(1)"/>
<br />
<br />
 <img src="https://github.com/user-attachments/assets/a3aab588-86a4-4e5e-b9f5-2b24bc2b9beb" height="80%" width="80%" alt="Routing and remote access(2)"/>
<br />
<br />
 <img src="https://github.com/user-attachments/assets/b3182b9d-ce3c-4c76-9bb9-e63a71633bb0" height="80%" width="80%" alt="Routing and remote access(3)"/>
<br />
<br />
 <img src="https://github.com/user-attachments/assets/a6e66503-c9c3-46cb-9fc7-c4c2c2ecd785" height="80%" width="80%" alt="Routing and remote access(4)"/>
<br />
<br /> 
  </li>

 # Setting up DHCP
<li> Next we will set up DHCP for IP address assignment by the domain controller.For setting up these services most of the intial steps are similar and this is no different. So on the server manager dashboard Select Add roles and feaures > Click on next a couple of times until you arrive at Select server role. At this point check the DHCP server box. Select the add features button. And Press Next a couple of times until the installation window where you click install and allow it to install. The screenshots highlight the following steps
<img src="https://github.com/user-attachments/assets/3c664273-50b7-4e5d-9dcf-a002d84b8a4b" height="80%" width="80%" alt="DHCP server installation(0)"/>
<br />
<br />
<img src="https://github.com/user-attachments/assets/323fedf5-b35d-4fa7-bad2-65a33e668d93" height="80%" width="80%" alt="DHCP server installation(1)"/>
<br />
<br />
<img src="https://github.com/user-attachments/assets/17319d40-64fa-4c19-83d0-ca1e3a2dec89" height="80%" width="80%" alt="DHCP server installation(2)"/>
<br />
<br />
The next step would be to set up DHCP scope.For this on the server dashboard  select tools > DHCP.Notice the DHCP server is now named as dc.mydomain.com. Upon clicking it we note that that both the IPv4 and IPV6 icons are down(denoted by the red dot as show below)
<br />
<br />
<img src="https://github.com/user-attachments/assets/6e00b886-58a4-4040-9e79-d8e89c7387bb" height="80%" width="80%" alt="DHCP scope(0)"/>
<br />
<br />
Right click on the IPv4 Icon and select new scope and this should lead you into the New Scope Wizard. When prompted to provide a name for the scope for this lab we will name the scope after the IP ranges which for us will be 172.16.0.100-200 and click next as shown
below.(You can leave the description blank)
<br />
<br />
<img src="https://github.com/user-attachments/assets/6acc1b0e-0760-4e98-ab1d-83b85013d96c" height="80%" width="80%" alt="DHCP scope(1)"/>
<br />
<br />
 The next step wil be to provide the IP range for our case our start IP address will be 172.16.0.100 and our end address will be 172.16.0.200.Our subnet maskt should be set 255.255.255.0 or /24 as well. This is shown in the screen shot below.
 <br />
<br />
 <img src="https://github.com/user-attachments/assets/b46df56d-72a8-458c-973d-87a38e4212e5" height="80%" width="80%" alt="DHCP scope(2)"/>
<br />
<br />
 For the Add exclusions and Delay do not provide information and select Next as for this lab we do not want to add any exclusions.
 <br />
 <br />
 For lease durations (which denotes how long a certain device can have an IP addressed before the it is dropped and returned to the Pool and the device there after would need to request for a new IP address) in our use case we will allow the lease duration to remain at 8 days.Do this and then click next
 <br />
<img src="https://github.com/user-attachments/assets/ebd4002d-12de-48b4-b428-18ec759ac4cb" height="80%" width="80%" alt="DHCP scope(3)"/>
<br />
<br />
 For configure DHCP Options Select the Yes, I want to configure these options now option.
 <br />
 <br />
 For the Router/Default Gateway provide the IP address for the DC 172.16.0.1 and select the add button. as shown below.
 <img src="https://github.com/user-attachments/assets/fab7b9ee-919b-4ba0-b8e3-b8bd39a8108d" height ="80%" width="80%" alt="DHCP scope(4)">
 <br />
 <br />
 In the Domain Name and DNS server section there is no need to provide any information as just press Next. This is because the DC server will act as the DNS server as shown below.
  <img src="https://github.com/user-attachments/assets/516dad97-3c5d-4e70-81fd-a6416918a194" height ="80%" width="80%" alt="DHCP scope(5)">
<br />
<br />
 Skip the WINS server section and just click next.
 <br />
 <br />
 When asked if you want to activate the scope now select the yes option and finally click on Finish.
 <br/>
 <br />
 The final step would be to right click the DHCP server and select authorize, then right click the DHCP server again and select refresh. If the process was smooth the IPv4 and IPv6 icons should light up green as shown in the screenshot below.
 <br />
 <br />
   <img src="https://github.com/user-attachments/assets/1c15ea0d-3e3f-427f-aa38-30573fe28471" height ="80%" width="80%" alt="DHCP scope(6)successful configuration of DHCP">
 </li>

 # Using Powershell to add users to the Domain.
 <li>
  The first thing we wil do here is donwload the zip from the following site https://github.com/joshmadakor1/AD_PS/archive/master.zip in our Domain controller and extract the files as shown below.(if we run into trouble with browsing on Internet explorer which we
  most likely will, go to configure this local server on server manager.Look for IE Enhanced Security configuration and turn it off, this is not something that would be recommended for an actual production)
  <br/>
     <img src="https://github.com/user-attachments/assets/ebc8a491-831b-456e-a620-c1bc6ddc425c" height ="80%" width="80%" alt="Powershell(0)">
     <br />
     <br />
 </li>
 <li>
  Once we extract the AD_PS master folder onto the Desktop we open the names.txt folder and add our names onto it(it can be any name).This is the file our powershell script will obtain names from to add users onto our domain.This is shown below: ensure you save
  the changes you make to this file.
  <br />
  <img src="https://github.com/user-attachments/assets/43b7a949-35a4-4f48-9c18-d2911e7e7c32" height ="80%" width="80%" alt="Powershell(1)">
     <br />
     <br />
 </li>
 <li>
  Next navigate to Windows Powershell ISE(click on start > Windows Powershell > Windows Powershell ISE) once here. Right click  Windows Powershell ISE and select more and then Run as administrator as show below.
  <br />
    <img src="https://github.com/user-attachments/assets/620ead2e-fce4-4270-b2aa-372e9962f6a6" height ="80%" width="80%" alt="Powershell(2)">
  <br />
  <br />
 </li>
 <li>
  Inside Windows Powershell script at the top bar select the open script button denoted by a yellow folder icon and navigate to the AD_PS master file and then to the CREATE USERS file that you had earlier downloaded(it is in the same folder as the names file).This has been demonstrated below:
  <br />
   <img src="https://github.com/user-attachments/assets/5cfca9d2-a2e2-45f2-97a5-28d333d8b2e5" height ="80%" width="80%" alt="Powershell(3)">
  <br />
  <br />
 </li>
 <li>
  Before we can run out script,security features of our server will prevent this from happening and so to get around thise we need to run the command <code>Set-ExecutionPolicy Unrestricted</code> and when asked about the execution policy change select the
  Yes to all option as shown below.
  <br />
   <img src="https://github.com/user-attachments/assets/acfad5e1-28b3-4852-9715-b6f939764971" height ="80%" width="80%" alt="Powershell(4)">
  <br />
  <br />
 </li>
 <li>
  The final thing before we run the script is to navigate to the directory the file names is (which should be in the same directory as the CREATE USERS AD_PS master) To do this enter the command<code> cd(for change direcrory)  C:\Users\(username for me it was a-pisaac)\Desktop(or Downloads depending on where you stored this file)\AD_PS-master</code>. We can then run the <code>ls</code> command to verify that names.txt is in the directory. The screenshot below showes this information
  <br />
   <img src="https://github.com/user-attachments/assets/1a9941ad-bc0b-4eaa-8668-c2f57c7f4285" height ="80%" width="80%" alt="Powershell(5)">
  <br />
  <br />
 </li>
 <li>
  To run the script press the green play button at the top bar and when prompted with the security warning  select the Run once option.
     <img src="https://github.com/user-attachments/assets/f4cb7b12-ee8e-43fd-b284-830abff6f1ee" height ="80%" width="80%" alt="Powershell(6)">
     <br />
     <br />
 </li>
 <li>
  If the above steps went well we see the following display as the accounts are created as a result of running the powershell script
  <img src="https://github.com/user-attachments/assets/cb2c7b0b-0155-43cf-a380-948093c13141" height ="80%" width="80%" alt="Powershell(7)">
     <br />
     <br />
 </li>
 <li>
  To confirm that new users have been added to our domain we can navigate to Active Directory Users and computers and in our domain which in our case is (mydomain.com) under USERS we should be able to view a list of many new users added to the domain as shown
  below.
  <img src="https://github.com/user-attachments/assets/d92f9f59-95cf-47be-be6d-41c81e744c3c" height ="80%" width="80%" alt="Powershell(8)">
     <br />
     <br />
 </li>

 # Creating the Windows 10 client
 <li>
  The steps here will be a bit similar to how we set up our server on oracle. Here We can name our windows machine client1 doesn't really matter to be honest. We can also ensure we provide the path file for our ISO Image As shown below
  <img src="https://github.com/user-attachments/assets/11c1499a-f373-41ba-ae31-915eb64991d1" height ="80%" width="80%" alt="Windows10vm(0)">
     <br />
     <br />
 </li>
<li>
 When it comes to RAM allocation as mentioned earlier  we will need to have both machines running at the same time so be mindful if the total ram allocated to both machines is more than 50% of  you entire RAM one of the machines will automatically shut down so to avoid this depending on your device allocate RAM sparingly. 
<img src="https://github.com/user-attachments/assets/503af122-cd15-48e5-9506-65e795190632" height ="80%" width="80%" alt="Windows10vm(1)">
     <br />
     <br />
</li>
<li>
 Navigate to Network and change your network adapter from NAT to being attached to Internal Network this is because we are trying to obtain an IP address from our Domain controller as our DHCP server. This has been illustrated below.
 <img src="https://github.com/user-attachments/assets/0e829cd0-cc5f-448b-b024-442123398e9b" height ="80%" width="80%" alt="Windows10vm(2)">
     <br />
     <br />
</li>
<li>
 Honorable mention. Incase you're asked for a product key you can indicate you lack one.
</li>
<br/>
<br/>
<li>
 For selecting the Operating system you wasnt to install Select the WINDOWS 10 prov version as shown.
  <img src="https://github.com/user-attachments/assets/b0d45ce2-86e1-4aa3-900e-cef3387a6686" height ="80%" width="80%" alt="Windows10vm(3)">
     <br />
     <br />
</li>
<li>
When asked whether you want to add a second keyboard layout we can just select skip
  <img src="https://github.com/user-attachments/assets/ec55ca7b-846b-4a0e-b569-69a304f6460b" height ="80%" width="80%" alt="Windows10vm(4)">
     <br />
     <br />
</li>
<li>
 When we are askt to connect to a network select the I don't have internet option at the bottom
 part of the scren as show below.
  <img src="https://github.com/user-attachments/assets/bd40d34f-bb9c-433a-a6f5-0561159ef1db" height ="80%" width="80%" alt="Windows10vm(5)">
     <br />
     <br />
</li>
<li>
 On the next Window that says there is more to discover select the continute with limted setup option at the bottom left portion of your screen
 <img src="https://github.com/user-attachments/assets/5b1c7c8e-78e4-4357-bacb-ac53105e18c9" height ="80%" width="80%" alt="Windows10vm(6)">
     <br />
     <br />
</li>
<li>
 On the next Window that is asking who is using the PC we can indicate "user"
 <img src="https://github.com/user-attachments/assets/e9a3c47e-228c-439e-b462-7c6655f22a0b" height ="80%" width="80%" alt="Windows10vm(7)">
     <br />
     <br />
</li>
<li>
 On the next Window that asks for  a password we probably don't need a password for now
 so you can just click on next leaving the space blank"
 <br />
 <br />
 <img src="https://github.com/user-attachments/assets/b0acf9a0-cd5a-4944-a436-2cb5679e196f" height ="80%" width="80%" alt="Windows10vm(8)">
     <br />
     <br />
</li>
<li>
 The final step of our project is to test the connectivity on ourclient. on the windows10 client ping a certain website for in this case we decided to ping
 google with the following command <code>ping www.google.com</code> and if all has gone well you should recieve a reply proving that the DNS, DHCP, RAT/NAS and AD DS configurations are okay.Thanks for getting this far into my project I hope you had fun!

 <br />
 <br />
 <img src="https://github.com/user-attachments/assets/68ecd58f-204e-4b50-83ba-78eaa11b2f21" height ="80%" width="80%" alt="Windows10vm(9)">
     <br />
     <br />
</li>

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
