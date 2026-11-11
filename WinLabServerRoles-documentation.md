# Oracle VirtualBox Snapshots
Before installing anything, IT IS IMPORTANT TO TAKE SNAPSHOTS OF YOUR VMS IN CASE OF VM FAILURES  

<table>
  <tr>
    <td align="center">
      <img src="screenshots/2-VirtualBox-SnapShot.png" width="1000">
      <br>
      <em>SnapShot Feature Located Top Left</em>
      <br><br>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="screenshots/3-VirtualBox-SnapShot.png" width="1000">
      <br>
      <em>SnapShot Interface</em>
      <br><br>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="screenshots/4-VirtualBox-SnapShot.png" width="1000">
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
  <img src="screenshots/5-DC1-AddRoles.png" width="600">
  <br>
  <em>Add Roles and features</em>
</p>

4) At the "Installation Type" window, ensure that Role-Based or feature-based installation is selected
5) At the "Server Role" window, check the Active Directory Domain Services and DNS Server boxes

    - A window will appear asking to install additional features for both Active Directory Services and DNS Server boxes. INSTALL THE ADDITIONAL FEATURES

<p align="center">
  <img src="screenshots/6-DC1-AddFeatures.png" width="600">
  <br>
  <em>Additional Features</em>
</p>

6) At the "Confirmation" window, review the roles being installed and install them
7) Afterwards, a warning should appear top right, stating "Promote this server to a domain controller"

<p align="center">
  <img src="screenshots/7-DC1-PostInstall.png" width="600">
  <br>
  <em>Post Install</em>
</p>

8) The Active Directory Domain Services Configuration Wizard should appear. Select the "Add a new forest" button and name your root domain as desired
    - We are adding a new forest because this is a completely new IT environment and establishes the first domain

<p align="center">
  <img src="screenshots/8-DC1-DomainName.png" width="600">
  <br>
  <em>Active Directory Domain Services Configuration Wizard</em>
</p>

9) At the "Domain Controller Options" window, ensure that the first two boxes are selected and input your desired password for DSRM
    - DNS is selected because it provides name resolution for AD
    - GC is selected because it provides searchable information
    - RODC is NOT selected because it provides a READ-ONLY copy of your server      

<p align="center">
  <img src="screenshots/9-DC1-DomainControllerOptions.png" width="600">
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

# Test Connectivity between VMs  