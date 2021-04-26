---
title: "StackPath Service: Connect to VMs and containers"
slug: stackpath-connect-to-vms-and-containers
---

## Connecting to a VM

A virtual machine in a StackPath workload may be reached using a standard SSH client.

### Prerequisites

1. You must have the private key counterpart of the public key that was used when the VM was created.  The private key was generated with the public key, and is usually a file that begins with the string `-----BEGIN RSA PRIVATE KEY-----`.
1. There must be an inbound network rule in *Network policies* for this workload, allowing TCP traffic originating from the IP that you are connecting from, on port 22.
1. You must know the default username for the operating system running on the VM.  See *List of default usernames* below.

### Identify the target IP address

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The *Details* screen will appear.
1. Click on the *Instances* item on the left.  A list of the instances deployed in the workload will appear.
1. Identify the desired instance, and note its public IP address in the list.  Clicking directly on the IP address will copy it to your clipboard.
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

## Connecting to a container

A container in a StackPath workload may be reached using a standard SSH client to connect to the StackPath remote access proxy.

### Enable remote management

Remote management must be enabled for the desired workload.  If remote management is already enabled, skip to the next section, *BLA*.

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The details screen will appear.
1. Click on the *Settings* item on the left.  The settings screen will appear.
1. Find the setting for *Remote management*.  Move the slider to the enabled position, if it is not already.
![Enable remote management](../../assets/sp-connect-enable-remote-mgt-en.png)

### Connect to the console

1. Navigate to the StackPath environment containing the desired workload.
1. Click on the workload to see its details.  The details screen will appear.
1. Click on the *Instance* item on the left.  A list of the instances deployed in the workload will appear.
1. Identify the desired instance, and click on the three-dot menu on the far right of the row.
1. Click on *Access console*.
1. The *Access console* dialog box will appear, and the command `/bin/bash` will be pre-populated in the **Command to run** text field.  Click *Submit*.
1. A notification will appear, with two important items, an SSH command and a password.
   - Click on the clipboard icons to the right of each item to copy the SSH command and the password into your clipboard.
   - The SSH command is intended to be executed from a Unix command line, such as in the MacOS or Linux Terminal application.
   - Windows users can use their preferred SSH client for Windows. Use the port number and hostname from the command, with `/bin/bash` as the remote command to execute.
1. Once you have executed the SSH command and entered the password (or configured your Windows SSH client and opened the connection), you will have a command prompt within the target container.
