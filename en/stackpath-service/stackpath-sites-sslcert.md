---
title: "StackPath Service:  How to set up SSL for your site"
slug: stackpath-how-to-setup-ssl
---


StackPath enables full support for SSL (HTTPS) connections for your sites.  Even if your origin servers are not configured to serve content via SSL, StackPath can provide SSL termination for your front-end, with no need to change your existing server configuration.  You can use your own SSL certificate, or StackPath can generate one for you.  For your convenience, the edge address for your delivery domain (eg, `xyz123.stackpathcdn.com`) by default has a valid SSL certificate installed for HTTPS connections.

Users must have the *User* role or higher, and be a member of the target environment with the environment role *Editor* or *Owner* to manage a StackPath site's SSL certificates.

Navigate to the desired StackPath service, click on the desired environment, click on the tab labeled *Sites*, click on the desired site, and then click on the *EdgeSSL* item to manage your site's SSL certificates.  The site must have at least one StackPath service enabled in order for the *EdgeSSL* item to appear on this page.  

### Add a third-party certificate

If you already own a valid, signed SSL certificate for your site, it can be used to for your StackPath site.  You will need the SSL certificate itself, as well as the private key used to originally generate the Certificate Signing Request (CSR) for this certificate.  When your certificate was issued, the signing authority may have provided a set of certificates with your signed certificate, called a CA bundle.  If a CA bundle was provided (also referred to as `intermediary certificates`), it must be included when uploading the certificate.  The CA bundle is an important part of establishing a chain of trust, and if it is required but not uploaded here, your end-users will receive warnings from their browsers that an intermediary SSL certificate is missing.

1. From the *EdgeSSL* screen, click on the button labeled *Upload certificate*.  The *Create third party certificate* screen appears.
1. Paste your certificate, including the lines `-----BEGIN CERTIFICATE-----` and `-----END CERTIFICATE-----`, into the *Certificate* text box.
1. Paste the private key, including the lines `-----BEGIN PRIVATE KEY-----` and `-----END PRIVATE KEY-----`, into the *Private key* text box.
1. As described above, if a CA bundle, or intermediary certificates, were provided by your signing authority, paste them in the order they were provided into the *CA bundle* text box.
1. Click *Submit*.  You will be taken back to the *EdgeSSL* page.
1. The certificate will appear momentarily.  Details on the certificate will be provided, as well as the delivery domain(s) that will be served with this certificate.

![Upload certificate](../../assets/sp-sites-edgessl-uploadcert-en.png)

### Request a certificate

1. From the *EdgeSSL* screen, click on the button labeled *Request certificate*.  The *Request free certificate* screen appears.
1. The default delivery domain for your site will appear in the *Delivery domains* field.  Click the `+` button to add additional delivery domains to the SSL certificate.
1. Select the method to validate the certificate:
  - **DNS:** StackPath will validate your ownership of the domain by performing a DNS lookup against the delivery domain.  If the delivery domain is already configured to point to the StackPath edge address, the ownership condition will be satisfied.
  - **HTTP:** StackPath will validate your ownership of the domain by connecting to the delivery domain and making an HTTP request.  If the request is served by a StackPath edge server, the ownership condition will be satisfied.
 1. Click *Submit*.  You will be returned to the *EdgeSSL* screen.
 1. The SSL certificate will be requested and installed.  When this is complete, it will be displayed on the *EdgeSSL* screen, as well as the delivery domain(s) that will be served with this certificate.

![Request certificate](../../assets/sp-sites-edgessl-requestcert-en.png)

### EdgeSSL options

#### Minimum TLS version

TLS is the protocol that is used to establish SSL connections.  This option specifies the oldest version of TLS that will be allowed to connect to your StackPath site.  We recommend that you select TLS 1.2, unless you have a specific need for supporting older browsers.

![Minimum TLS version](../../assets/sp-sites-edgessl-mintls-en.png)

#### Force HTTPS

This option will force all HTTP connections to redirect to your site using SSL.

![Force HTPS](../../assets/sp-sites-edgessl-forcessl-en.png)

### Delete a certificate

1. From the *EdgeSSL* screen, click on the three-dot action menu on the right-hand side of the installed certificate.
1. Click *Delete*.
1. A confirmation dialogue box will appear.  Click *Submit* to confirm.
1. The certificate will be deleted from the site.
