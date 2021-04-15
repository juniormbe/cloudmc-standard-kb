---
title: "StackPath Service: How-to for CDN"
slug: stackpath-cdn-howto
---

Different ways to affect cache performance.

Cache TTL
DNS TTL

##### How do I set up my site?

##### How do I set up DNS A record to StackPath Edge server?
1. Log in to your domain provider (e.g. GoDaddy)
1. Find and click on each of your domains below
1. Find DNS Settings or just Settings
1. Look for Records and update them so they point to your site's Edge address as follows: acme.cloud.ca
Type	Name	Value
A	@	151.139.128.10
1. All done! (it can take up to 24 hours for the change to take effect)  The amount of time for the change to propogate could be as long as the value of the TTL field in the domain's SOA record.

##### How do I set up multiple origins for content?

##### How do I manually purge all assets from the cache and force assets to be reloaded?
1. Click on the *Sites* tab.
1. Click on the desired site.
1. Click on the *CDN* item on the left.
1. Click on the *Purge CDN* button.
1. When the button expands, click *Purge everything*.
1. A dialog box will appear asking for confirmation.  Click *Submit*.
1. The CDN cache will be purged.

##### How do I choose CDN settings that can help me with SEO optimization?

Summary

Required permissions

Navigate to

*Document specification:* StackPath Service: Sites How-to

*Overview:* KB article to ...

*Description of target audience:* CloudMC Users.  Technical but less experienced.

*Languages:* English, French

*Non-goals:*

*Estimated length:* Single article / Multiple articles

*Finer points:*

*Outline of document:* Sections for each function

*Reviewers and their responsibilities:*

*Outstanding issues:*

*Schedule:* By 14 April
