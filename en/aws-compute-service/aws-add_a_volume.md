---
author: "AWS: Add a volume"
publisher: aws-add-a-volume
---

# AWS: Add a volume

## About this task

This article will guide you through the process of adding a new volume to an AWS environment.

## Before you begin

-   Your AWS environment must already exist

## Procedure

1.  Navigate to the desired environment. The **Instances** page appears.

2.  Click on the **Volumes** item. A list of volumes in this environment appears.

3.  Click on the **Add Volume** button. The **Add Volume** wizard appears.

4.  Configure the new volume:

    1.  Enter a name into the **Name** field, or accept the default.

    2.  Select the volume type to create.

    3.  Enter the number of gigabytes to allocate for the new volume into the **Size** text box. The volume must be an integer.

    4.  Select the availability zone where the new volume should be created.

        The choice of availability zone will determine the instances to which the new volume may be attached.

5.  \(Optional\) You can automatically attach the new volume to an existing instance:

    1.  Click on **Attach volume to existing instance**.

    2.  A list of instances in the selected availability zone will appear. Select the desired instance.

    3.  Enter the desired device name into the text box labeled **Device Name**.

6.  Click the **Submit** button.


## Results

-   The volume of the specified size is created in the active environment
-   It exists in the selected availability zone
-   If an instance was selected, the volume is automatically attached to that instance
-   The volume is listed in the **Volumes** screen of the **Compute** tab

## Example: Add a volume

### About this task

In this example, we will add a new volume to the Acme `production` AWS environment. We will add a general purpose 10GB volume to the `us-east-1b` availability zone, and automatically attach it to our instance `acme-prod-db01`.

### Before you begin

-   The Acme `production` environment must already exist
-   The instance `acme-prod-db01` must already exist in the `us-east-1b` availability zone

### Procedure

1.  Navigate to the Acme `production` environment. The **Instances** page appears.

2.  Click on the **Volumes** item. A list of volumes in the environment appears.

3.  Click on the **Add Volume** button. The **Add Volume** wizard appears.

4.  Configure the new volume:

    1.  Enter `acme-prod-vol01` into the **Name** field.

    2.  Select `General Purpose SSD (gp2)` for the volume type.

    3.  Enter `10` into the **Size** text box.

    4.  Select the `us-east-1b` availability zone.

5.  We will configure the new volume to be attached to our instance:

    1.  Click on **Attach volume to existing instance**.

    2.  Select `acme-prod-db01` from the list of instances.

    3.  Enter `/dev/sdf` into the text box labeled **Device Name**.

6.  Click the **Submit** button.


### Results

-   Our new volume `acme-prod-vol01` of 10GB is created in the Acme `production` environment
-   It exists in the `us-east-1b` availability zone
-   The volume has been automatically attached to the instance `acme-prod-db01`
-   The volume is listed in the **Volumes** screen of the **Compute** tab

