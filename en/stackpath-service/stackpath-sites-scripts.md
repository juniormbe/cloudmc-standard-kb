---
title: "StackPath Service:  Serverless Scripts"
slug: stackpath-serverless-scripts
---


StackPath can make your JavaScript code available for execution with no additional work.  Simply upload the script to your StackPath site, specify the endpoint at which the script should be made available, and that's it, users can send requests to your script while StackPath takes care of deployment and execution.

Serverless Scripts are deployed globally on StackPath's edge network, and are executed in a dedicated sandbox JavaScript engine.  A script is executed for each request, and the script terminates once the request is served -- scripts do not run continuously in the background.

Users must have the *User* role or higher, and be a member of the target environment with the environment role *Editor* or *Owner* to manage StackPath Serverless Scripts.

Navigate to the desired StackPath service, click on the desired environment, click on the tab labeled *Sites*, click on the desired site, and then click on the *Scripts* item to manage your site's WAF settings.  The site must have the Scripts service enabled in order for the *Scripts* item to appear on this page.  

### Add a script

1. From the *Scripts* page, click the button labeled *Add script*.  The *Add script* page will appear.
1. Enter a name for the script in the text box labeled *Name*.  This name is used only for identifying the script within the interface and API.
1. In the text box labeled *Routes*, enter the identifier that your end-users will use to make requests to your script.  The string entered into this box will be appended to the hostname of the site, to form a unique URL for the endpoint.
   - The string must use valid percent-encoding (URL encoding).  Invalid syntax will be rejected when the page is submitted.
   - Forward slashes ('/') are allowed in the identifier.
   - If desired, an additional identifier may be added by clicking the plus ('+') icon to the right of the text box.  An identifier that is no longer needed may be removed by clicking the minus ('-') icon.
1. Enter the JavaScript code into the text box labeled *Code*.
1. Click *Submit*.
1. Your script will now be deployed to your site, and is accessible using the specified endpoint.

![Add script](../../assets/sp-sites-scripts-echoserver-en.png)

#### Test the script

The specified endpoint will be combined with the site's hostname to form the URL that can be used to access the script.  For example, if the hostname of a site is `www.acme.com` and a script is uploaded with the route `echoserver`, that script will be accessible at `http://www.acme.com/echoserver`.  Test your script by navigating to that URL in a browser and verifying that the script returns the desired results.

### Edit a script

1. From the *Scripts* page, identify the script to be edited.
1. Click on the three-dot action menu on the right-hand side of the desired script.
1. Click on *Edit*.  The *Edit* screen will appear.
1. Make the desired changes, and click *Submit* when done.
1. The changes will be saved and you will be returned to the *Scripts* page.  Changes to the name or endpoint will be reflected here.

### Delete a script

1. From the *Scripts* page, identify the script to be deleted.
1. Click on the three-dot action menu on the right-hand side of the desired script.
1. Click *Delete*.
1. A confirmation dialogue box will appear.  Click *Submit* to confirm.
1. The script will be deleted.

<!-- ### Examples of JavaScript code -->
