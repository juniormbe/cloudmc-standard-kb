---
title: "StackPath Service: Sites overview"
slug: stackpath-sites-overview
---


### What are StackPath sites, and how do they help me?

**Sites** are how we control the delivery of content through the StackPath network.  This includes configuration of features available through the Content Delivery Network (CDN), as well as Web Application Firewall (WAF), and Serverless Scripting.

A site acts as the bridge between servicing the requests from users via one or more *Delivery domains*, and grabbing the static *assets* for those requests from the servers where the assets are hosted, called the *origin*.  It's a quick and easy way to improve your application performance.

The reason you need a delivery domain specifically for assets is because dynamic content will continue to come from your own servers, which is easy to do simply by using different domain names for dynamic vs static content.

#### Content Delivery Network (CDN)

The crucial part is that the CDN will store a site's assets in caches on the StackPath Edge servers.  The StackPath global network is then able to accelerate the delivery of the assets from the cache to users, enhancing performance and user experience.

The site features allow administrators to configure the origin where assets are pulled from, the length of time to store them in the cache, as well as other behaviors.

Have to be strategic with your use of caching.  Higher cache TTLs will reduce the number of times the CDN will pull the assets from origin, however it also means that without manually clearing the cache, an update to an asset will take longer to propagate to end users.  Can go with origin's cache control, or define in your site's CDN settings.

Can put the CDN in front of your object storage.  Or in front of your SP// workload.

It's really important to have your Web server at the origin be configured to server assets with the correct headers.

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
