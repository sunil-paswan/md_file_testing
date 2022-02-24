Lab Requirement: Azure Free Account.
------------------------------------

Estimated time to complete this lab: 30 minutes.
------------------------------------------------

—----------------------------------------------------------------------------------------------------------------------------

Azure Free Account Setup Procedure:

If you already have a Microsoft Azure subscription, you can skip this section.
------------------------------------------------------------------------------

Otherwise, follow below steps to create a free trial subscription. You will need to provide a valid credit card number for verification, but you will not be charged for Azure services.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. If you already have a Microsoft account that has not already been used to sign up for a free Azure trial subscription, you’re ready to get started. If not just create a new Microsoft account.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2. After you’ve created a Microsoft account, create your free Microsoft Azure account. You’ll need to sign-in with your newly created Microsoft account. Then you’ll need to:
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

• Enter your phone number to verify your identity.
--------------------------------------------------

• Enter the code you have been sent to verify it.
-------------------------------------------------

• Provide valid payment details. This is required for verification purposes only.
---------------------------------------------------------------------------------

Note: Your credit card won’t be charged for any services you use during the trial period, and the account is automatically deactivated at the end of the trial period.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

—----------------------------------------------------------------------------------------------------------------------------

Let’s Get Started!
------------------

Objective:
----------

Deploy Azure VMs in High Availability (Deploy Azure VMs in An
Availability Sets and Availability Zones).

***Step 1: Deploy Azure VMs in Availability Sets with 99.95% SLA.***

**Perform the following steps:**

1\. Sign in to the Azure portal.

2\. In the Search bar, type Virtual Machines, and then click Add.

3\. On the Create virtual machine blade, give below details:

Click Basics.

Enter Unique VM Name

Enter VM disk type

Enter Username and Password

Select Subscription

Select or Create Azure Resource Group

Select Azure DataCenter Location (Region - East US)

4\. Select Availability Options to Add Availability Set.

Click Create New

> Type the name for the Availability set
>
> Select the no. of Fault Domains and Update Domain, Then click OK.

Fault domains – The group of VMs that share a common power source and
network switch. By default, the VMs are separated across up to three
fault domains and can be changed to between 1 and 3.

Update domains – Update domains indicate groups of virtual machines and
underlying physical hardware that can be rebooted at the same time. By
default, 5 domains are assigned. This can be set to between 1 to 20.

5\. Leave the rest tabs to their default values and select Review +
Create.

Now your First VM is created and deployed in an Availability Set.

### 

### **Create a Second Virtual Machine and Add to the same Availability Set:**

1\. Repeat the same steps from 1-3 of the previous VM creation.

2\. Select the Availability Set in the Availability Set option. (Existing
Availability Set)

NOTE: Second VM should be in the same Resource Group as the First VM.

3\. Leave the rest tabs to their default values and select Review +
Create.

Now you have successfully deployed both the VMs in the Availability Set.

4\. Check the status of the Availability Set by going into the Resource
Group and select the created Availability Set resource.

5\. Now you can see that both the Virtual Machines are deployed in the
Fault Domain and Update Domain.

***Step 2: Deploy Azure VMs in Availability Zones to Protect from
Datacenter Level Failures with 99.99% SLA.***

**Perform the following steps:**

1\. Sign in to the Azure portal.

2\. In the Search bar, type Virtual Machines, and then click Add.

3\. On the Create virtual machine blade, give below details:

Click Basics.

Enter Unique VM Name

Enter VM disk type

Enter Username and Password

Select Subscription

Select or Create Azure Resource Group

Select Azure DataCenter Location (Region- East US)

4\. Select Availability Options to Add Availability Zone.

Select the 1st Availability Zone for your first VM from the Availability
Zone options.

NOTE: Not every region has support for Availability Zones. A region can
have up to 3 max. Availability Zones.

5\. Move to the Disks tab and leave this with the default values.

6\. Networking Tab.

7\. Select Create New on the Public IP option and choose Zone-redundant
in the Create public IP address page and click OK.

(This will make your VM available for zone redundancy otherwise the VM
will behave like in an Availability Set).

8\. Select Review + Create tab, then Create.

Now we have successfully deployed your First VM in the first
Availability Zone of the East US region.

### 

### 

### 

### 

### 

### **Create a Second Virtual Machine and Add to the second Availability Zone in the Azure Portal:**

1\. Repeat the same steps from 1-3 of the previous VM creation.

2\. This time select the second Availability Zone for your second VM from
the Availability Zone options.

3\. Repeat the same steps from 5-6 of the previous VM creation.

4\. Leave the rest tabs to their default values and select Review +
Create tab, then Create.

Now you have successfully deployed your VMs in the Availability Zone of
the East US region.
