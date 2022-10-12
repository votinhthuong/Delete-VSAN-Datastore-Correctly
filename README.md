Enable SSH on ESXi host where you deploy VCSA

Log in ESXi host suing IP address and root and password.
Click Manage on Navigator part.
Select the Services tab.
Select TSM-SSH service from the list.
Push Start button on top.

Connect with root user to ESXi host using PuTTy, command prompt, Terminal, PowerShell, Chrome SSH or whatever you have.

Type the following command to check out the vSAN Datastore.

esxcli vsan storage list

If you have any storage linked to vSAN, delete it with the following command. Make sure you select the right UUID of the vSAN Datastore.

esxcli vsan storage remove -u "UUID"

The command will list all the vSAN mounted storage on ESXi host. If you don’t have any mounted datastore like my lab, just type the following command to remove the host from vSAN cluster.

esxcli vsan cluster leave

The task has been completed. Now you should have a healthy ESXi host with any notifications or the “Found host(s) esxi.mydomain.lab participating in the vSAN service which is not a member of this host’s vCenter cluster” error.
