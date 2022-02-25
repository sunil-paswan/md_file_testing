Lab Requirement: Azure Free Account.
Estimated time to complete this lab: 45-60 minutes.
—--------------------------------------------------------------------------------------------------------------

Azure Free Account Setup Procedure:

If you already have a Microsoft Azure subscription, you can skip this section.
Otherwise, follow below steps to create a free trial subscription. You will need to provide a valid credit card number for verification, but you will not be charged for Azure services.
If you already have a Microsoft account that has not already been used to sign up for a free Azure trial subscription, you’re ready to get started. If not just create a new Microsoft account.
After you’ve created a Microsoft account, create your free Microsoft Azure account. You’ll need to sign-in with your newly created Microsoft account. Then you’ll need to:
• Enter your phone number to verify your identity.
• Enter the code you have been sent to verify it.
• Provide valid payment details. This is required for verification purposes only.

Note: Your credit card won’t be charged for any services you use during the trial period, and the account is automatically deactivated at the end of the trial period.
—----------------------------------------------------------------------------------------------------------------

Let’s Get Started!
Objective:
Demonstrate load balancing on a web server using Azure standard load balancer.

In this hands-on lab you will be creating below components:

1. Create Azure load balancer
2. Create a virtual network
3. Create a backend pool
4. Create health probes
5. Create a load balancer rule
6. Setup two new windows VM
7. Install IIS for Testing
8. Add virtual machines to the backend pool
9. Testing
---------------------------------------------

Task 1: Create Azure load balancer

Step 1) Log in to Azure Portal.
Step 2) On top use the search bar and search for Load Balancer and then choose Load Balancer.
Step 3) On the top left-hand side of the screen, click Add
Step 4) In the Basics tab of the Create load balancer page, enter or select the following information, accept the defaults for the remaining settings, and then select Review + create.
Subscription: Select your subscription.
Resource group: Select Create new and type LBresourcegroup in the text box.
Name: Enter myLoadBalancer
Region: Select East US
Type: Select Public.
SKU: Select Basic
Public IP address: Select Create new. If you have an existing Public
IP you would like to use, select Use existing.
Public IP address name: Type myPublicIP in the text box.
Step 5) Now Click On Create and check your Load Balancer Is Created.

Task 2: Create a Virtual Network
Step 1) On the upper-left side of the screen, select Create a resource > Networking > Virtual network or search for Virtual network in the search box.
Step 2) In Create virtual network, enter or select the following information in the Basics tab.
Step 3) Select the Next: IP Addresses button. In the IP Addresses tab, enter information.
Step 4) Under Subnet name, select the word default. In the Edit subnet, enter below information and select Save then select the Review + create tab.
Subnet name: myBackedSubnet
Subnet address range: 10.0.0.0/24

Task 3: Create a Backend Pool
A backend address pool contains the IP addresses of the virtual (NICs) connected to the load balancer.
Step 1) Select All services in the left-hand menu, select All resources, and then select myLoadBalancer from the resources list.
Step 2) Under Settings, select Backend pools, then select Add.
Step 3) In the Add a backend pool page, enter the below information and then select Add.
Name: myBackendPool
Virtual Network: myVNet (LBresourcegroup)
IP Version: IPv4
Associated to: Virtual Machines

Task 4: Create a Health Probe
The load balancer monitors the status of your app with a health probe. The health probe adds or removes VMs from the load balancer based on their response to health checks.
Step 1) Select All services in the left-hand menu, select All resources, and then select myLoadBalancer from the resources list.
Step 2) Under Settings, select Health probes, then select Add.
Step 3) Enter the below information in the Add health probe page and then select OK.
Name: myHealthProbe
Protocol: HTTP
Port: 80
Path: /
Interval: 15
Unhealthy threshold: 2

Task 5: Create a Load Balancer Rule
A load balancer rule is used to define how traffic is distributed to the VMs. You define the frontend IP configuration for the incoming traffic and the backend IP pool to receive the traffic. The source and destination ports are defined in the rule.
Step 1) Select All services in the left-hand menu, select All resources, and then select myLoadBalancer from the resources list.
Step 2) Under Settings, select Load balancing rules, then select Add.
Step 3) Use these values to configure the load-balancing rule and then select OK.
Ip version: ipv4
Front end ip address: load balancer front end
Protocol: TCP
Port: 80
Backend port: 80
Health probe: http:80
Session persistence: None
Idle time out: 15
Task 6: Setup Two New windows VM
Now you have to create two different ‘Windows Server’ Virtual Machines and to do so you can follow the steps given in this Documentation.

Note: Create both the VMs in an Availability Set and Select the previously created VNet named “myVNet” under the Networking tab.

Vnet name: myVNet
Subnet: myBackendSubnet (10.0.0.0/24)
Public ip: myVM1-ip
NIC nsg: basic
Public inbound ports: allow selected ports
Select inbound ports: HTTP:80, HTTPS:443, RDP: 3389
Task 7: Install IIS for Testing
Install IIS Web Server on the virtual machines to test the load balancer.

Step 1) Run the following command in the Azure Cloud Shell (PowerShell) to install IIS on the virtual machine. Change the Location and Resource Group parameter according to the VM in which you have deployed:

Set-AzVMExtension `
-ResourceGroupName LBresourcegroup `
-ExtensionName IIS `
-VMName myVM1 `
-Publisher Microsoft.Compute `
-ExtensionType CustomScriptExtension `
-TypeHandlerVersion 1.4 `
-SettingString ‘{“commandToExecute”:”powershell Add-WindowsFeature Web-Server; powershell Add-Content -Path \”C:\\inetpub\\wwwroot\\Default.htm\” -Value $($env:computername)”}’ `
-Location EastUS

Note: Change the -VMName line to “myVM2” for installing IIS on the second Virtual Machine.

Task 8: Add Virtual Machines to the Backend Pool
Step 1) Select All services in the left-hand menu, select All resources, and then select myLoadBalancer from the resources list.
Step 2) Under Settings, select Backend pools, then select myBackendPool.
Step 3) Select the myVNet in the Virtual Network and Select Virtual machines in Associated to.
Step 4) In the Virtual machines section, select + Add and then select the newly created both VMs, Select Save.

Task 9: Test the Load Balancer
Step 1) Find the public IP address for the load balancer on the Overview screen of the Load Balancer.
Step 2) Copy the public IP address, and then paste it into the address bar of your browser. Check the response. A valid response verifies that the load balancer was successfully created and can successfully connect with the backend VMs.

Refresh the browser multiple times and you should see connections to both myVM1 and myVM2.