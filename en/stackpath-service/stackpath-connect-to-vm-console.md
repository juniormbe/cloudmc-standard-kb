---
title: "StackPath Service: Connect to a workload VM console"
slug: stackpath-connect-to-vm-console
---


A virtual machine in a StackPath workload may be reached via its console by using a standard SSH client to connect to the StackPath remote access proxy.  The following procedure will guide you through the required steps.  Some temporary changes to the network policies for your workload may be necessary when connecting to the console for the first time.

### Prerequisites

Prior to connecting to the console, you will need to:

1. Enable remote management
1. Retrieve the password for your account
1. Connect to the target VM via SSH and configure the password on your user account

Once the password is set, you may then connect to the console of your virtual machine without repeating the above steps.

### Enable remote management

Remote management must be enabled for the desired workload.  Follow the procedure [Enable remote management](stackpath-enable-remote-mgt.md).  If remote management is already enabled, you may skip to the next section, *Retrieve the password for your account*.

### Retrieve the password for your account

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find a list of the instances deployed in the workload.
1. Identify the desired virtual machine, and click on the three-dot menu on the far right of the row.
1. Click on *Access console*.  The *Access console* dialogue box appears.
1. Select **Serial Console Connection**, then click *Submit*.
1. A notification will appear, with two important items, an SSH command and your password.  The SSH command may be ignored for now.  Make note of your password.  Clicking the clipboard icon to the right of the password will copy it to your clipboard.
![Notification](../../assets/sp-connect-notif-en.png)
1. You can close the notification.

### Set the password for your account

When the virtual machine for your workload was created, StackPath added the public key that was specified on the *Add workload* page into the default account on the new virtual machine.  You will need the private key of the key pair whose public key was used to create the VM in order to SSH to the VM and set the password for console access.

1. Follow the procedure [Connect to a workload VM using SSH](stackpath-connect-to-vm-via-ssh.md) to connect to the desired VM and get a root shell.
   - Depending on the existing network configuration of the target workload, you may need to add a network policy to allow TCP traffic on port 22 from your IP address.
   - The procedure will indicate which default username to use for your VM.  You will use the same username in the next step.
1. At the root shell, execute the command `passwd <username>`, where `<username>` is the default username for the OS running on the virtual machine.
1. When the `passwd` prompt appears, enter a secure password of your choice, followed by the `Enter` key.
1. Re-enter the password to confirm, followed by the `Enter` key.
1. You may now exit the root shell and close the SSH connection.

Example output of connecting to a virtual machine via SSH and setting the password for the `centos` user:
```
stefan@co-seguizabal ~ % ssh -i .ssh/stef.key centos@184.176.185.56
Last login: Wed May 19 21:24:07 2021 from 129.171.32.1
[centos@w-seguizabal-kwx-wi-seguizabal-zfb-phx-0 ~]$ sudo -i
[root@w-seguizabal-kwx-wi-seguizabal-zfb-phx-0 ~]# passwd centos
Changing password for user centos.
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
[root@w-seguizabal-kwx-wi-seguizabal-zfb-phx-0 ~]# logout
[centos@w-seguizabal-kwx-wi-seguizabal-zfb-phx-0 ~]$ logout
Connection to 184.176.185.56 closed.
stefan@co-seguizabal ~ %
```

**Note:** After successfully testing the connection in the next section, if a network policy was created to connect via port 22, it is important to delete that policy.

### Connect to the VM console

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find a list of the instances deployed in the workload.
1. Identify the desired virtual machine, and click on the three-dot menu on the far right of the row.
1. Click on *Access console*.  The *Access console* dialogue box appears.
1. Select **Serial Console Connection**, then click *Submit*.
1. A notification will appear, with two important items, an SSH command and your StackPath password.
   - Click on the clipboard icons to the right of each item to copy the SSH command and the StackPath password into your clipboard.
   - The SSH command is intended to be executed from a Unix command line, such as in the MacOS or Linux Terminal application.
   - Windows users can use their preferred SSH client for Windows. Use the port number and hostname from the proffered SSH command.
1. Once you have executed the SSH command (or configured your Windows SSH client and opened the connection), you will be prompted for your StackPath password.  Enter it now, and hit the `Enter` key.
1. You may have to hit `Enter` again to get a login prompt.  This is normal for a remote access proxy.
1. A login prompt for the target virtual machine will now appear.  Enter the username and hit the `Enter` key.
1. You will be asked for the password for this account.  Enter the password you set for the account, and hit the `Enter` key.
1. A command prompt within the target virtual machine now appears.  If root privileges are required, use the command `sudo -i` to get a root shell.
1. Delete the network policy that was created during the previous section, if applicable.
