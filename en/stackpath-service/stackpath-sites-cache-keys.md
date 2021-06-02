---
title: "StackPath Service: Cache keys"
slug: stackpath-sites-cache-keys
---


When the CDN needs to differentiate between assets that could be similar or identical, **cache keys** are the criteria that make an asset unique.  The CDN will examine these criteria for each asset and then store or discard accordingly.  For example, judging by filename alone, the CDN will consider `https://www.acme.com/image1.jpeg` and `https://www.acme.com/image2.jpeg` to be different assets, which is a reasonable assumption.  But what about a different situation, where we are passing query parameters?  For example, `https://www.acme.com/?qp=1` and `https://www.acme.com/?qp=2` would be treated by default as different assets.  However, you can define different parameters as cache keys for your site, and tell the CDN that these two requests are in fact for the same asset, despite having differing values for the `qp` query parameter.
