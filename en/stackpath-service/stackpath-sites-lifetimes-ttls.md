---
title: "StackPath Service: Lifetimes and TTLs"
slug: stackpath-sites-lifetimes-ttls
---


One of the most important settings to consider when configuring your site is the length of time after an asset has been stored in the cache before the CDN refreshes the asset from the origin.  This is called the **lifetime**, and is frequently referred to as the TTL, or *time to live*. Higher cache TTLs will reduce the number of times the CDN will pull the assets from origin, and it also means that without manually clearing the cache, an update to an asset will take longer to propagate to end users.  This is one of the ways that your deployments might be affected by the CDN -- if you make frequent changes to your assets, you may want to have a lower lifetime so that assets refresh more quickly.  On the other hand, if your assets never change, you may certainly benefit from a longer lifetime.

TTLs are enforced wherever there are cached assets, namely at the CDN and at the end-user's browser.  An unrelated TTL that often comes into play is for DNS records, and this is controlled by a domain's name servers.  The DNS TTL does not affect the expiration of assets, only the caching of a domain name, but it can impact your planning and deployments.  It is important not to confuse the two.
