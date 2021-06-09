---
title: "StackPath Service:  Custom images"
slug: stackpath-images
---


StackPath workloads provide you with the flexibility to easily deploy new virtual machine workloads based on the VMs you have already created.  Any existing virtual machine can be used as the base from which a *custom OS image* can be created.  Custom OS images can be used to reduce deployment time by acting as a fully-configure master that requires miminal changes to be ready for service. Custom OS images can also be used to roll back should a deployment experience an error or other failure.

An OS image is a copy of the root volume of a virtual machine.  It is stored on the StackPath compute nodes.  Please note that an image does not include any data volumes -- the image contains **only** the root volume of the original VM.

To create a StackPath custom OS image, an account with the *User* role must be a member of the environment which contains the workload, and also have the *Editor* or *Owner* environment role assigned.  An account with the *Administrator* role or higher may create, modify, or delete workloads in any environment.

To access images, navigate to the desired StackPath environment.  The *Edge compute* page will appear.  Click on the *Images* item on the left.  The *Images* screen will appear.

### Creating a custom OS image

#### Pre-requisites

- Begin by deploying a workload of type VM (virtual machine) in the desired StackPath environment.
- The VM may be deployed from either a standard OS image or a custom OS image.
- Configure the VM with the required software and updates, as needed.
- Complete any other desired modifications.
- Power off the VM.
   - Note that StackPath will automatically power down a running VM when creating an image for it.

#### Create the image

1. Once the virtual machine to be imaged is ready, click on the *Edge compute* workspace tab, and when the *Workloads* page appears, click on the *Images* item on the left.
1. From the *Images* page, click on the button labeled *Add custom image*.  The *Add custom image* page will appear.
1. In the text box labeled **Family**, we recommend you enter a name that describes the general operating system of the image, for example *centos-8* or *ubuntu-2004*.
1. In the text box labeled *Tag*, enter a name to identify this image, for example *frontend-master*.
1. Select the StackPath workload for the VM to be imaged from the popup list labeled **Source workload**.
1. Select the Stackpath instance to be imaged from the popup list labeled **Source instance**.
1. Enter an optional description in the text box labeled **Description**.  The description will be displayed with the image in the listing on the *Images* page.
1. Click *Submit*.  The virtual machine will now be shut down by StackPath, and the image will be taken.

**Note:** Once the image is ready, be sure to start the source virtual machine if it should be running.

### Listing custom images

Navigate to the desired environment and click on it.  The *Edge compute* page will appear.  Click on the *Images* item on the left.  The *Images* screen will appear, listing all available images.  Custom OS images will appear at the bottom.  The names of custom images will appear in the format `environment/family:tag`.

### Deploying from a custom OS image

To use a custom OS image when deploying a new virtual machine workload, follow the steps in the [Managing workloads](stackpath-managing-workloads.md) knowledge base article.  When choosing OS image, click on the **Custom OS images** section and select the desired image from the list that appears.

<!-- An image of the Custom OS image group will go here once I can take a nice screenshot. -->
