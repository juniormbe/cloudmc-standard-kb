---
author: "Subnetworks"
publisher: aws-subnetworks
---

# Subnetworks

A subnetwork is a portion of an AWS VPC that can be used to deploy instances. A single subnetwork may use a part of the IP range of its VPC, or it may use the VPC's full IP range.

Like a VPC, a subnetwork is defined using a CIDR. The CIDR of the subnetwork must exist entirely within the CIDR of the VPC, and it must not overlap the CIDR of any other subnetwork within the same VPC. A subnetwork exists within a single AWS availability zone.

The choice of subnetwork will determine the availability zone for an instance. This impacts which volumes are available to attach to an instance.

Subnetworks are found in the **Networking** tab of your AWS environment. Find the desired VPC and click on the **Subnetworks** feature to see a complete list.

**Parent topic:**[Networking](aws-networking.md)

