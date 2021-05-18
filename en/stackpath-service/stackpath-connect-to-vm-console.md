---
title: "StackPath Service: Connect to a VM console"
slug: stackpath-connect-to-vm-console
---


## Connecting to a VM via the console

A virtual machine in a StackPath workload may be reached via its console by using a standard SSH client to connect to the StackPath remote access proxy.

Prior to connecting to the console for the first time, you will need to:
1. Enable remote management
1. Retrieve the password for your account
1. Connect to the target VM via SSH and configure the password on your user account

Once the password is set, you may then connect to the VM console.  The following procedure will guide you through these steps.

### Retrieve the password for your account

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find a list of the instances deployed in the workload.
1. Identify the desired virtual machine, and click on the three-dot menu on the far right of the row.
1. Click on *Access console*.  The *Access console* dialogue box appears.
1. Select **Serial Console Connection**, then click *Submit*.
1. A notification will appear, with two important items, an SSH command and a password.  The SSH command may be ignored for now.  Make note of the password on line 3.  (Clicking the clipboard icon to the right of the password will copy it to your clipboard.)
![Notification](../../assets/sp-connect-notif-en.png)
1. You can close the notification.

### Set the password for your account

When the virtual machine for your workload was created, StackPath added the public key that was specified on the *Add workload* page into the default account in the new virtual machine.  You will need the private key in order to SSH to the VM and set the password for console access.

1. Follow the procedure in the section above, *Connecting to a VM using SSH*, to connect to the desired VM and get a root shell.
1. At the root shell, execute the command `passwd <username>`, where `<username>` is the default username for the OS running on the virtual machine.
1. When the `passwd` prompt appears, enter the StackPath password that you obtained above, followed by the `Enter` key.
1. Re-enter the password to confirm, followed by the `Enter` key.
1. You may now exit the root shell and close the SSH connection.

### Connect to the VM console

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find a list of the instances deployed in the workload.
1. Identify the desired virtual machine, and click on the three-dot menu on the far right of the row.
1. Click on *Access console*.  The *Access console* dialogue box appears.
1. Select **Serial Console Connection**, then click *Submit*.
1. A notification will appear, with two important items, an SSH command and a password.
   - Click on the clipboard icons to the right of each item to copy the SSH command and the password into your clipboard.
   - The SSH command is intended to be executed from a Unix command line, such as in the MacOS or Linux Terminal application.
   - Windows users can use their preferred SSH client for Windows. Use the port number and hostname from the proffered SSH command.
1. Once you have executed the SSH command and entered the password (or configured your Windows SSH client and opened the connection), you will have be prompted for your StackPath password.  Enter it now, and hit the `Enter` key.
1. A login prompt for the target virtual machine will now appear.  Enter the username and hit the `Enter` key.
1. You will be asked for the password for this account.  Enter your StackPath password and hit the `Enter` key.
1. A command prompt within the target virtual machine now appears.  If root privileges are required, use the command `sudo -i` to get a root shell.

### Post-configuration cleanup

If direct access via SSH to the target virtual machine is not necessary, be sure to remove the network policy for TCP port 22 for this workload.
