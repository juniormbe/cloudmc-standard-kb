---
title: "Security groups"
slug: aws-security-groups
---


Security groups are sets of rule that provide control over network access to your resources in an AWS environment.

When deploying a new instance, the **Add instance** wizard presents three choices:

-   **Allow traffic from all sources**

    The security group will allow ingress traffic from all IP addresses, for all protocols and port numbers.

-   **Enable traffic only for HTTP, HTTPS, and SSH**

    This will create a security group which denies all ingress traffic except for TCP ports 22, 80, and 443. Enter a name and description for the groups, or accept the defaults.

-   **Configure a custom security group policy**

    You can specify an IP address or a CIDR block, protocol, and port numbers to be allowed ingress. Enter a name and description for the security group, or accept the defaults, then enter the criteria for the group.


**Parent topic:**[Networking](aws-networking.md)

