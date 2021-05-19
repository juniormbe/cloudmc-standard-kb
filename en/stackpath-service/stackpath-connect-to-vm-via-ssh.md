---
title: "StackPath Service: Connect to a workload VM using SSH"
slug: stackpath-connect-to-vm-via-ssh
---


A virtual machine deployed in a StackPath workload may be reached using a standard SSH client.  This procedure will guide you through the steps of identifying the IP address of your target VM and then connecting to the VM with an SSH client, using your private key.

### Prerequisites

1. There must be an inbound network rule in *Network policies* for this workload, which allows TCP traffic originating from the IP that you are connecting from, on port 22.
1. You must know the default username for the operating system running on the VM.  See *List of default usernames* below.
1. To log into the VM, you must have the private key from the same key pair whose public key was used when the VM was created.  The private key is usually a file that begins with the string `-----BEGIN RSA PRIVATE KEY-----`.

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

### Common errors

The following are common errors that your SSH client may return when attempting to connect to your virtual machine.

1. **Operation timed out:**  Check your *Network policies* page to verify that there is an inbound rule that allows TCP traffic on port 22, originating from the IP address that you are connecting from.
1. **Permission denied:**  Verify that you are using the correct private SSH key that corresponds to the public SSH key that was used to create the target VM.
