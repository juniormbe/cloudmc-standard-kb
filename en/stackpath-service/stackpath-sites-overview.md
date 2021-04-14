---
title: "StackPath Service: Sites overview"
slug: stackpath-sites-overview
---


### What are StackPath sites?

**Sites** are how we control the delivery of content through the StackPath network.  This includes configuration of features available through the Content Delivery Network (CDN), as well as Web Application Firewall (WAF), and Serverless Scripting.

A site acts as the bridge between servicing the requests from users via one or more *Delivery domains*, and requesting the static *assets* for those requests from the server where the assets are hosted, called the *origin*.  This mechanism makes it quick and easy to improve your application performance, and also to manage the  .

The delivery domain provides a necessary abstraction layer, because dynamic content will continue to come from your own servers.  The delivery domain make this simple by using different domain names for dynamic vs static content.

#### Content Delivery Network (CDN)

The crucial part is that the CDN will store a site's assets in caches on the StackPath Edge servers.  The StackPath global network is then able to accelerate the delivery of the assets from the cache to users, enhancing performance and user experience.

The site features allow administrators to configure the origin where assets are pulled from, the length of time to store them in the cache, as well as other behaviors.

Have to be strategic with your use of caching.  

Can put the CDN in front of your object storage.  Or in front of your SP// workload.

It's really important to have your Web server at the origin be configured to server assets with the correct headers.

##### Cache keys
When the CDN needs to differentiate between assets that could be similar or identical, **cache keys** are the criteria that make an asset unique.  The CDN will examine these criteria for each asset and then store .  For example, http://www.example.com/page.html would be considered by search engines to be an entirely different page from http://www.example.com/page.html?parameter=1, even though both URLs may reference the same content.[5][6]

##### TTLs and expirations
Higher cache TTLs will reduce the number of times the CDN will pull the assets from origin, however it also means that without manually clearing the cache, an update to an asset will take longer to propagate to end users.  Can go with origin's cache control, or define in your site's CDN settings.

TTLs are enforced wherever there are caches that store assets, namely at the CDN and at the end-user's browser.  An unrelated TTL that often comes into play is for DNS records, and this is controlled by a domain's name servers.  The DNS TTL does not affect the expiration of assets.

<!--
#### Web Application Firewall (WAF)

Controls the kinds of HTTP requests that can come in based on criteria such as headers and query parameters.
-->


### See also

### External links


Doc spec:

*Document specification:* Article name here

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
