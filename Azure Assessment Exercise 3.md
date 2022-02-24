Lab Requirement: Azure Free Account.
------------------------------------

Estimated time to complete this lab: 45 minutes.
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

Deploy Azure VMs in Backup policies and restore from the last restore
point.

**Step 1: Create a Backup of a VM**
-----------------------------------

Create a simple scheduled daily backup to a Recovery Services Vault.

1\. Sign in to the Azure portal.

2\. In the menu on the left, select Virtual machines.

3\. From the list, select a VM to back up. (Existing VMs or Create New)

4\. On the VM blade, in the Operations section, click Backup.

5\. Then the Enable backup blade opens.

6\. In the Recovery Services vault, click Create new and provide the name
for the new vault.

(A new vault is created in the same resource group and location as the
virtual machine).

7\. Under Choose backup policy, keep the default (New) DailyPolicy or
Create New and then click Enable Backup.

8\. To create an initial recovery point, on the Backup blade click Backup
now.

10\. On the Backup Now blade, click the calendar icon, use the calendar
control to choose how long the restore point is retained, and click OK.

11\. In the Backup blade for your VM, you’ll see the number of restore
points that are complete.

The first backup takes about 15-20 minutes. Proceed to the next section
of this assessment after your backup is finished.

**Step 2: Recover VM from your Backup Vault**
---------------------------------------------

1.  Navigate to the Backup center in the Azure portal and click Restore
    > from the Overview tab.

<!-- -->

1.  Select Azure Virtual machines as the Datasource type, and then
    > select a Backup instance.

2.  Select a VM and click Continue.

3.  In the next screen that appears, select a restore point to use for
    > the recovery.

**Choose a VM restore configuration**
-------------------------------------

1.  In Restore Virtual Machine, select a restore option:

    -   Create new: Use this option if you want to create a new VM.

2.  Specify settings for your selected restore option.

**Create a VM from restore point**
----------------------------------

As one of the [restore
options](https://docs.microsoft.com/en-us/azure/backup/backup-azure-arm-restore-vms#restore-options),
you can create a VM quickly with basic settings from a restore point.

1.  In Restore Virtual Machine &gt; Create new &gt; Restore Type, select
    > Create a virtual machine.

2.  In Virtual machine name, specify a VM that doesn't exist in
    > the subscription.

3.  In the Resource group, select an existing resource group for the new
    > VM, or create a new one with a globally unique name.

4.  In Virtual network, select the VNet in which the VM will be placed.
    > All VNets associated with the subscription in the same location as
    > the vault, (which is active and not attached with any affinity
    > group), Select the subnet.

5.  In Staging Location, specify the storage account for the VM.

6.  Select Restore to trigger the restore operation.
