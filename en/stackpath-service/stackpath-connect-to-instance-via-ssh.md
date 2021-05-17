---
title: "StackPath Service: Connect to VMs and containers"
slug: stackpath-connect-to-vms-and-containers
---

## Connecting to a VM using SSH

A virtual machine in a StackPath workload may be reached using a standard SSH client.

### Prerequisites

1. You must have the private key counterpart of the public key that was used when the VM was created.  The private key was generated with the public key, and is usually a file that begins with the string `-----BEGIN RSA PRIVATE KEY-----`.
1. There must be an inbound network rule in *Network policies* for this workload, allowing TCP traffic originating from the IP that you are connecting from, on port 22.
1. You must know the default username for the operating system running on the VM.  See *List of default usernames* below.

### Identify the target IP address

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find a list of the instances deployed in the workload.
1. Identify the desired instance, and note its public IP address in the list.  Clicking on the clipboard icon to the right of the IP address will copy it to your clipboard.
![Instance public IP](../../assets/sp-connect-instance-public-ip-en.png)
1. You are now ready to connect to the instance.  The procedure is different when using a standard Unix command line client (this includes macOS) versus a Windows SSH client.

#### Standard Unix command line SSH client (including macOS)

1. Begin by opening a terminal window.
1. The private key should be present in your `~/.ssh` directory.  The file containing the private key must have permissions of `0644`.  To set the correct permissions, use the command `chmod 644 <filename>`.
1. The general form for using a private key to connect to a remote host via SSH is: `ssh -i <keyfile> username@IP`. The key must be specified with a path if the key is not in the current working directory.  For example, if connecting to an Ubuntu instance at 151.139.189.1, and the key file is in `~/.ssh/my.key`, use the following command:
   ```
   ssh -i ~/.ssh/my.key ubuntu@151.139.189.1
   ```
1. You should now be connected to the VM and see a command prompt.  If root privileges are required, use the command `sudo -i` to get a root shell.

#### Windows SSH client

This a generic procedure for using a Windows SSH client.  It may be necessary to first convert the private key and then install the key into the client.  See the user manual for your SSH client for the exact procedure.

1. Open a new connection in your SSH client.
1. Select **SSH** as the connection type.
1. Enter the IP address of the VM into the **Host Name** (or **IP address**) field.
1. Enter the default username into the **Username** or **Login as** field.
1. At this point, you will have to supply the private key or have it already installed, as mentioned in the note above.  See the user manual for your SSH client.
1. Click **Connect** or **Open**.
1. You should now be connected to the VM and see a window with a command prompt.  If root privileges are required, use the command `sudo -i` to get a root shell.

### List of default usernames

| OS name | Default username |
| --- | --- |
| CentOS | centos |
| Debian | debian |
| Ubuntu | ubuntu |

## Connecting to a VM via the console

A virtual machine in a StackPath workload may be reached via its console by using a standard SSH client to connect to the StackPath remote access proxy.

Prior to connecting to the console for the first time, you will need to:
1. Enable remote management
1. Retrieve the password for your account
1. Set that password on your user account.

Once the password is set, you may then connect to the VM console.

### Enable remote management

Remote management must be enabled for the desired workload.  If remote management is already enabled, skip to the next section, *Connect to the VM console*.

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find the setting for *Remote management*.  Move the slider to the enabled position, if it is not already.
![Enable remote management](../../assets/sp-connect-enable-remote-mgt-en.png)

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
1. Once you have executed the SSH command and entered the password (or configured your Windows SSH client and opened the connection), you will have be prompted for your SteckPath password.  Enter it now, and hit the `Enter` key.
1. A login prompt for the target virtual machine will now appear.  Enter the username and hit the `Enter` key.
1. You will be asked for the password for this account.  Enter your StackPath password and hit the `Enter` key.
1. A command prompt within the target virtual machine now appears.  If root privileges are required, use the command `sudo -i` to get a root shell.

## Connecting to a container

A container in a StackPath workload may be reached using a standard SSH client to connect to the StackPath remote access proxy.

Remote management must be enabled for the desired workload.  If remote management has not been enabled, refer to the section above, *Enable remote management*.  If remote management is already enabled, skip to the next section, *Connect to the container console*.

### Connect to the container console

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Scroll down to find a list of the instances deployed in the workload.
1. Identify the desired container, and click on the three-dot menu on the far right of the row.
1. Click on *Access console*.
1. The *Access console* dialog box will appear, and the command `/bin/bash` will be pre-populated in the **Command to run** text field.  Click *Submit*.
1. A notification will appear, with two important items, an SSH command and a password.
   - Click on the clipboard icons to the right of each item to copy the SSH command and the password into your clipboard.
   - The SSH command is intended to be executed from a Unix command line, such as in the MacOS or Linux Terminal application.
   - Windows users can use their preferred SSH client for Windows. Use the port number and hostname from the proffered SSH command, with `/bin/bash` as the remote command to execute.
1. Once you have executed the SSH command and entered the password (or configured your Windows SSH client and opened the connection), you will have a command prompt within the target container.
