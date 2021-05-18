---
title: "StackPath Service: Connect to a container"
slug: stackpath-connect-to-container
---


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
