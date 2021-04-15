---
title: "StackPath Service: CDN settings for sites"
slug: stackpath-cdn-settings
---


<!-- Summary

What can I break with each of these features?  Fortunately, nearly all of the settings function independently of each other, which makes it easier to tweak settings, measure the impact, and then decide whether to modify the setting again.  Also, most of these setting won't actually break anything, except for CORS support.
-->

The StackPath CDN feature settings are grouped into two sections.  The first section addresses cache handling, which controls how the CDN will make decisions on storing assets as well as how those assets will be delivered.  The second section includes policies for the client browser, which control how the CDN will tell the end-user's browser to handle assets.

Users must have the *User* role or higher, and be a member of the environment, and have the environment role *Editor* or *Owner* to manage StackPath sites.

Navigate to the desired StackPath service, click on the desired environment, and click on the tab labeled *Sites* to manage your sites.

#### Cache handling

- **Lifetime:**  If this option is set to *Origin controlled*, the CDN will pass along the cache-control headers set at the origin.  If set to *Specify CDN TTL*, a popup menu will appear, from which you may select a lifetime for static assets to be stored.  This will not affect caching of dynamic content, which will still be cached according to the cache-control headers set at the origin.  If *Never expire* is selected, static content will be stored in the cache and will not be refreshed until manually purged.  Finally, the *Do not cache* setting will prevent the CDN from storing any assets in the cache, and all requests will be served from the origin.
![Lifetime](../../assets/sp-cdn-lifetime-en.png)

- **Query string control:**  If this option is set to *Ignore query strings*, all are treated as same file, 2) *Cache all query strings* Track all query params, each is treated as a different file, 3) custom, can define which query params to track.  If set to *Custom*, a text box will appear where the names of the query params may be entered.  to track as keys for caching. Should I enable query string control?  If the content you're sending back to the browser is not affected by the values in your query parameters (or the presence of query parameters), then it's best to turn this off.
![Query string](../../assets/sp-cdn-querystring-en.png)

- **Dynamic caching by header:**  Make cache decision based on headers present in the request.  Has complicated implications.  Enabling this will give a text / popup field for entering the header names to use as cache keys
![Dynamic caching](../../assets/sp-cdn-dynamiccaching-en.png)

- **GZIP compression:**  The HTTP protocol allows a server to compress content before sending it in the response to the client.  Enabling this option will cause the CDN to compress content that isn't already compressed.  This   Compress text-type content by level 1 - 6.  Won't compress file types that are already compressed.  The recommended compression level is 6.  Also, won't compress content already stored in the cache, so you may wish to purge the cache to have this option take effect immediately.
![Gzip compression](../../assets/sp-cdn-gzip-en.png)

- Content persistence: If assets in the cache expire but the origin isn't reachable, the assets will be conserved in the cache and served to users until the origin is back.  This is a unique benefit of the StackPath CDN.

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
