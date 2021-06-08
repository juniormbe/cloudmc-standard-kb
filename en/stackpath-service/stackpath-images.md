---
title: "StackPath Service:  Custom images"
slug: stackpath-images
---


StackPath workloads provide you with the flexibility to easily deploy new virtual machines based on the VMs you have already created.  Any existing virtual machine can be used as the base from which a *custom OS image** can be created.  An image is a copy of the root volume of 

Root volume only



### Creating a custom OS image

Note: Powers off VM

Family name
Tag name
Select workload
Select source instance
Option description
Click *Submit*.  The virtual machine will now be shut down by StackPath, and the image will be taken.

Once the image is complete, be sure to start the virtual machine if it should be running.

### Listing custom images

Navigate to the desired environment and click on it.  The *Edge compute* page will appear.  Click on the *Images* item on the left.  The *Images* screen will appear, listing all available images.  Custom OS images will appear at the bottom.

### Deploying from a custom OS image

*Add workload*
Select the **Custom OS image** group.
Select the desired custom OS image.
[Managing workloads](stackpath-managing-workload.md)
