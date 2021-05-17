---
title: "StackPath Service:  Managing EdgeRules"
slug: stackpath-service-managing-edgerules
---


StackPath provides *EdgeRules* to give you control over how requests to your site are handled.  StackPath has four pre-defined EdgeRules that can be enabled, and also allows you to create custom EdgeRules to meet the specific needs of your site.

EdgeRules are available only when the CDN service is enabled for a site.  

that inspect requests to see if they match certain conditions, and matching requests will have actions applied to them.

Required permissions

Navigate to

### View EdgeRules

### Predeined EdgeRules

#### Force WWW connections
#### Custom robots.txt file
#### Pseudo-streaming
#### Referrer protection

- **Force WWW connections:**
- **Custom robots.txt file:**
- **Pseduo-streaming:**
- **Referrer protection:**

### Create a custom EdgeRule

The interface will present a text field for the name.  A condition type can be selected.  Upon selecting a condition type, the interface will display the options appropriate for the condition type.  Additionally, once a condition type is selected, the interface will display an action to select for the EdgeRule.  Depending on the selected action, the interface will show the appropriate options for the action.

### EdgeRule conditions

Conditions may use five different attributes for an EdgeRule.

- **URL:**
- **Header:**
- **HTTP method:**
- **Status code:**
- **Cookie:**

### EdgeRule actions

An EdgeRule may specify one of four general types of actions to execute when the condition is met.

- **Header rules:**
- **Caching rules:**
- **Redirect rules:**
- **URL signing:**

### See also

### External links
