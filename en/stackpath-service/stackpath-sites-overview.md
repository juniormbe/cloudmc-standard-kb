---
title: "StackPath Service: Sites overview"
slug: stackpath-sites-overview
---


### What are StackPath sites?

**Sites** are what you use to control the delivery of your content through the StackPath network.  This includes configuration of features available through the Content Delivery Network (CDN), as well as the Web Application Firewall (WAF), and Serverless Scripting.

A site in StackPath acts as a bridge between which services the requests from users via one or more *Delivery domains* on the front end, and which on the backend obtains the dynamic responses and the static *assets* for those requests from your server, called the *origin*.  This mechanism makes it quick and easy to improve your application performance, and also to apply settings uniformly to those domains, all under your control.

Because dynamic content will continue to come from your own servers, it is necessary to control how your services are delivered via the CDN.  The delivery domain makes this separation of services simple, by using your domain name for the front end, which increases customer confidence and assists with Search Engine Optimization (SEO).

#### Content Delivery Network (CDN)

As mentioned above, a site bridges the delivery of content from the origin to the end-user.  When properly configured, your end-users will access your application via the StackPath CDN without their knowing that there is an intermediary.  This is because the delivery domain will use a DNS record within your domain, rather than a StackPath domain.

For example, let's say that https://www.acme.com is currently served from your own servers.  This includes all content, both static and dynamic.  After full integration of the StackPath CDN with your site, your servers will act as the origin servers, and the CDN will be servicing requests

The CDN will store a site's assets in caches on the StackPath Edge servers.  The StackPath global network is then able to accelerate the delivery of the assets from the cache to users, enhancing performance and user experience.

The site features allow administrators to configure the origin where assets are pulled from, the length of time to store them in the cache, as well as other behaviors.

Have to be strategic with your use of caching.  

Can put the CDN in front of your object storage.  Or in front of your SP// workload.

Ideally is configured for HTTPS.

It's really important to have your Web server at the origin be configured to server assets with the correct headers.

##### Cache keys
When the CDN needs to differentiate between assets that could be similar or identical, **cache keys** are the criteria that make an asset unique.  The CDN will examine these criteria for each asset and then store .  For example, http://www.example.com/page.html would be considered by search engines to be an entirely different page from http://www.example.com/page.html?parameter=1, even though both URLs may reference the same content.[5][6]

##### TTLs and expiration times
Higher cache TTLs will reduce the number of times the CDN will pull the assets from origin, however it also means that without manually clearing the cache, an update to an asset will take longer to propagate to end users.  Can go with origin's cache control, or define in your site's CDN settings.

TTLs are enforced wherever there are caches that store assets, namely at the CDN and at the end-user's browser.  An unrelated TTL that often comes into play is for DNS records, and this is controlled by a domain's name servers.  The DNS TTL does not affect the expiration of assets.

<!--
#### Web Application Firewall (WAF)

Controls the kinds of HTTP requests that can come in based on criteria such as headers and query parameters.
-->
