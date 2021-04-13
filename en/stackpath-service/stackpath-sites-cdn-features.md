---
title: "StackPath Service: CDN settings for sites"
slug: stackpath-cdn-settings
---


Summary

What can I break with each of these features?  Fortunately, nearly all of the settings function independently of each other, which makes it easier to tweak settings, measure the impact, and then decide whether to modify the setting again.  Also, most of these setting won't actually break anything, except for CORS support.

Required permissions
Users must have the *User* role or higher, and be a member of the environment, and have the environment role *Editor* or *Owner* to manage StackPath sites.

Navigate to the desired StackPath service, click on the desired environment, and click on the tab labeled *Sites* to manage your sites.

### Feature overview

The CDN feature settings are grouped into two sections.  The section on cache handling controls how the CDN will make decisions on storing assets and how it will deliver those assets.  The section on client browser policy controls how the CDN will tell the end-user's browser to handle assets.

#### Cache handling

When the CDN needs to differentiate between assets that could be similar or identical, **cache keys** are the criteria that make an asset unique.  The CDN will examine these criteria for each asset and then store .  For example, http://www.example.com/page.html would be considered by search engines to be an entirely different page from http://www.example.com/page.html?parameter=1, even though both URLs may reference the same content.[5][6]

- Lifetime / TTL: Length of time an asset will be stored in the cache before the CDN refreshes the asset from the origin.
![Lifetime](../../assets/sp-cdn-lifetime-en.png)
- Query string control: 1) Ignore all query params, all are treated as same file, 2) Track all query params, each is treated as a different file, 3) custom, can define which query params to track.  Enabling option 3 will give a text / popup field for entering the names of the query params to track as keys for caching. Should I enable query string control?  If the content you're sending back to the browser is not affected by the values in your query parameters (or the presence of query parameters), then it's best to turn this off.
![Query string](../../assets/sp-cdn-querystring-en.png)
- Dynamic caching by header: Make cache decision based on headers present in the request.  Has complicated implications.  Enabling this will give a text / popup field for entering the header names to use as cache keys
![Dynamic caching](../../assets/sp-cdn-dynamiccaching-en.png)
- GZIP compression: Compress text-type content by level 1 - 6.  Won't compress file types that are already compressed.  The recommended compression level is 6.
- Content persistence: If assets in the cache expire but the origin isn't reachable, the assets will be conserved in the cache and served to users until the origin is back.
![Gzip compression](../../assets/sp-cdn-gzip-en.png)
- Use Vary header: What is the Vary header?  In this context, it means we can tell the cache a to keep list of headers that the origin server uses to make a decision on what content to return to the client. Enabling this tells the cache a to keep list of headers that the origin server uses to make a decision on what content to return to the client.  The vary header is a response header that that server puts into the response and it's a list of those headers.
![Vary header](../../assets/sp-cdn-vary-en.png)
- Canonical header:  Useful for search engines and SEO.  Adds the Link header and defines the asset as canonical.  This helps in the SP// CDN context because the asset is being served through a domain name that may or may not match what's in the HTML, and including this header will tell the search engine what this document actually represents.
- URL caching: Copied from SP// site b/c I don't really get this one: This feature allows caching of URLs without file extensions. By default, the StackPath CDN caches static content such as images, CSS and Javascript files. When enabling URL Caching, use-cases that desire to cache the entirety of a website's assets (including dynamic content) can be fulfilled.
![URL caching](../../assets/sp-cdn-urlcaching-en.png)

#### Client browser policy

- Browser cache TTL: Allows you to control how long the browser will store an asset in its local cache before the asset expires.  Enabling this injects the HTTP cache-control headers into responses with the specified time to live, however this will NOT override a cache-control header if it's already present in the response from the origin server.  This applies ONLY to assets that don't have a Cache-Control header already set by the origin server.  When enabled, the default is one hour.  
![Browser cache TTL](../../assets/sp-cdn-browsercachettl-en.png)
- CORS header support <- By default, a browser that downloads JavaScript from a site will not allow that script to request resources from any site other than the site the script came from.  Enabling this feature and specifying "All origins" injects the `Access-Control-Allow-Origin` header with a value of "*", which tells the browser to allow cross-origin requests to this site from all domains.  Selecting the option "Specify origins" gives a text / popup field for entering a list of domains that the browser may allow cross-origin requests to this site.  Disabling this feature will allow only the default behavior, with no cross-origin requests allowed. (Inserts the header for allowing browsers to access this domain from all or selected domains.  I think the thing to remember here is that the CORS stuff is just headers and resources being given to the browser, but all the CORS stuff is being evaluated from the browswer's perspective.)  
![CORS support](../../assets/sp-cdn-corssupport-en.png)
- HTTP/2 support: Enables the CDN to allow requests using the HTTP/2 protocol, which is supported by all major Web servers, CDNs, and Web browsers.
![HTTP/2 support](../../assets/sp-cdn-http2support-en.png)
- HTTP/2 server push:  Enables the CDN to push assets to the browser prior to the browser requesting them.  This can help improve performance on sites with pages that have no third-party content, such that a requested page and all its assets are sent in a single response, or on sites that have a clear likely click-through path, where most users are likely to click on a given page.  The headers must be configured properly at the origin server.
![HTTP/2 Server Push](../../assets/sp-cdn-http2serverpush-en.png)


*Document specification:* StackPath Service: Sites and CDN features

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
