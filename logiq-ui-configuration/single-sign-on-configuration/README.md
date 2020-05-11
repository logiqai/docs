---
description: SSO configuration details.
---

# Single Sign-On with SAML

## IDP configuration

Setting up SAML requires configuration on the identity provider \(IDP\) e.g. Okta or Google. Please refer to identity providers documentation. In your IDP application, provide the SAML Assertion Consumer Service \(ACS\) url for your LOGIQ environment and attribute mappings 

Following attributes are required. The LOGIQ mappings for each of the attributes are in brackets. Please use the correct attribute name otherwise LOGIQ will not be able to recognize the SAML assertion

* First name \(FirstName\) and Last name \(LastName\)
* Group name **** \(LogiqGroup\)

Use following SAML Assertion Consumer Service \(ACS\) url 

{% hint style="info" %}
_https://**&lt;LOGIQ UI IP/Domain&gt;**/saml/callback?org\_slug=default_
{% endhint %}

With this you should be able to access a SAML metadata URL or SAML metadata file.

## LOGIQ UI configuration

Login with your admin credentials. Click on "_Settings"_ menu. Enable _"SAML configuration"_ checkbox.   
Add SAML **Metadata URL, Entity ID, NameID Format** from Step [IDP Configuration ](./#idp-configuration)above.

## Login using SSO credentials

Logout from the LOGIQ UI and go back to the login screen. SAML login option should now be available. Click the _"SAML login"_ button and browser is redirected to the IDP screen where you login using your IDP credentials.

## Google SAML video

{% embed url="https://www.youtube.com/watch?v=pTVHkxcp4mg" %}



