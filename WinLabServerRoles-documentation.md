# Oracle VirtualBox Snapshots
Before installing anything, IT IS IMPORTANT TO TAKE SNAPSHOTS OF YOUR VMS IN CASE OF VM FAILURES  

<table>
  <tr>
    <td align="center">
      <img src="screenshots/02-VirtualBox-SnapShot.png" width="1000">
      <br>
      <em>SnapShot Feature Located Top Left</em>
      <br><br>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="screenshots/03-VirtualBox-SnapShot.png" width="1000">
      <br>
      <em>SnapShot Interface</em>
      <br><br>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="screenshots/04-VirtualBox-SnapShot.png" width="1000">
      <br>
      <em>SnapShot Success</em>
      <br><br>
    </td>
  </tr>
</table>

Do this with Server1 VM
!!! Before configuring a VM, it is best practice to take a snapshot !!!


# Installing Server Roles on DC1  
1) Start Up DC1 VM  
2) Navigate to Server Manager Application  
3) Click on "Add Roles and features"

<p align="center">
  <img src="screenshots/05-DC1-AddRoles.png" width="600">
  <br>
  <em>Add Roles and features</em>
</p>

4) At the "Installation Type" window, ensure that Role-Based or feature-based installation is selected
5) At the "Server Role" window, check the Active Directory Domain Services and DNS Server boxes

    - A window will appear asking to install additional features for both Active Directory Services and DNS Server boxes. INSTALL THE ADDITIONAL FEATURES

<p align="center">
  <img src="screenshots/06-DC1-AddFeatures.png" width="600">
  <br>
  <em>Additional Features</em>
</p>

6) At the "Confirmation" window, review the roles being installed and install them
7) Afterwards, a warning should appear top right, stating "Promote this server to a domain controller"

<p align="center">
  <img src="screenshots/07-DC1-PostInstall.png" width="600">
  <br>
  <em>Post Install</em>
</p>

8) The Active Directory Domain Services Configuration Wizard should appear. Select the "Add a new forest" button and name your root domain as desired
    - We are adding a new forest because this is a completely new IT environment and establishes the first domain

<p align="center">
  <img src="screenshots/08-DC1-DomainName.png" width="600">
  <br>
  <em>Active Directory Domain Services Configuration Wizard</em>
</p>

9) At the "Domain Controller Options" window, ensure that the first two boxes are selected and input your desired password for DSRM
    - DNS is selected because it provides name resolution for AD
    - GC is selected because it provides searchable information
    - RODC is NOT selected because it provides a READ-ONLY copy of your server      

<p align="center">
  <img src="screenshots/09-DC1-DomainControllerOptions.png" width="600">
  <br>
  <em>Domain Controller Options</em>
</p>

10) At the "Prerequisites Check" window, view the results and install when ready
    - A warning about the authoritative parent zone will appear. THIS IS OKAY SINCE THIS IS THE FIRST DOMAIN CONTROLLER AND DNS SERVER
    - The DC1 will restart

<p align="center">
  <img src="screenshots/10-DC1-PreReqCheck.png" width="600">
  <br>
  <em>Prerequisites Check</em>
</p>

# Installing Server Roles on Server1  
1) Start Up Server1 VM  
2) Navigate to Server Manager Application  
3) Click on "Add Roles and features"
4) At the "Installation Type" window, ensure that Role-Based or feature-based installation is selected
5) At the "Server Role" window, check the DHCP Server Box

    - A window will appear asking to install additional features for DHCP. INSTALL THE ADDITIONAL FEATURES

<p align="center">
  <img src="screenshots/11-Server1-AddFeatures.png" width="600">
  <br>
  <em>Additional Features (DHCP)</em>
</p>

6) At the "Confirmation" window, review the role being installed and install it
7) Afterwards, click on "Complete DHCP Configuration"
  - If you accidentally close it, a warning symbol should appear top right asking to complete DHCP Post Install

<table>
  <tr>
    <td align="center">
      <img src="screenshots/12-Server1-PostInstall.png" width="400">
      <br>
      <em>Post Install (DHCP) from Wizard</em>
    </td>
    <td align="center">
      <img src="screenshots/13-Server1-PostInstall.png" width="400">
      <br>
      <em>Post Install (DHCP) from menu</em>
    </td>
  </tr>
</table>

8) At the "DHCP Post-Install configuration wizard" window, click Commit

<p align="center">
  <img src="screenshots/14-DHCP-PostInstallWizard.png" width="600">
  <br>
  <em>DHCP Post-Install Wizard</em>
</p>

# Domain-Join Server 1 to DC1
1) On the Server 1 VM, type into the Windows Search Bar "View advanced system settings"

<p align="center">
  <img src="screenshots/15-Server1-AdvancedSettings.png" width="600">
  <br>
  <em>This window should appear</em>
</p>

2) Click on the "Computer Name" tab

<p align="center">
  <img src="screenshots/16-Server1-ComputerSettings.png" width="600">
  <br>
  <em>This menu should appear</em>
</p>

3) Click on "Change" button

4) In the "Computer Name/Domain Changes" window, under the "Member of" section, select the "Domain" radio button and input the domain name

<p align="center">
  <img src="screenshots/17-Server1-DomainJoin.png" width="600">
  <br>
  <em>Domain-Joined Server 1</em>
</p>

5) "Windows Security" window appears, input the DOMAIN ADMINISTRATIVE credentials
  - Domain Administrative credentials varies from organization to organization

<table>
  <tr>
    <td align="center">
      <img src="screenshots/18-Server1-AdminCredentials.png" width="400">
      <br>
      <em>Domain Admin Credentials</em>
    </td>
    <td align="center">
      <img src="screenshots/19-Server1-Joined.png" width="400">
      <br>
      <em>Confirmed Credentials</em>
    </td>
  </tr>
</table>

6) Restart Server 1 VM

# Test and Verify Winlab Setup
Start Up DC1
Within Server Manager, click on "Tools" top right
Click on Active Directory Users and Computers
Click on Computers and look for Server1

<p align="center">
  <img src="screenshots/20-DC1-Check.png" width="600">
  <br>
  <em>Server1 populates within DC1</em>
</p>

Start up Server1
Go back the advanced settings
Review the new computer name settings

<p align="center">
  <img src="screenshots/21-Server1-Check.png" width="600">
  <br>
  <em>Server 1 Computer Name Change</em>
</p>

Conduct ping tests to ensure connectivity
<p align="center">
  <img src="screenshots/22-PingTests.png" width="600">
  <br>
  <em>DC1 Ping Tests</em>
</p>