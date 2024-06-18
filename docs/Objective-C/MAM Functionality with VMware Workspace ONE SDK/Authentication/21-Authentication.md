---
layout: page
title: Authentication
hide:
  #- navigation
  - toc
---

The VMware Workspace ONE SDK for iOS (Objective-C) provides helper classes to authenticate credentials against Workspace ONE UEM.

An application can limit its access to users by integrating user authentication. Users authenticate to the Workspace ONE UEM console, whether it is a basic enrollment user or an Active Directory account. Authentication allows your application to follow enforced corporate security policies.

Configure the type of authentication the SDK profile uses to communicate with the application.

* Single Sign-On and the VMware Workspace ONE SDK for iOS (Objective-C)
  
  To use single sign-on (SSO), an SDK-enabled app must interact with the Workspace ONE Intelligent Hub for handling authentication across multiple apps. After initialization, the app can establish an SSO session with the Workspace ONE Intelligent Hub.
* Active Directory Password Changes
  
  If an Active Directory (AD) password changes and becomes out of sync with the object account of the SDK, use an API to update the SDK credentials.
* Authentication Type
  
  Authentication Type controls how applications that use the SDK framework to use authenticate to resources. Configure it to work with the SDK default setting for Single Sign-On (SSO) or on its own.
* SSO Session and the Workspace ONE Intelligent Hub
  
  A single sign-on (SSO) session establishes when a user authenticates with an application participating in in SSO. The session is active until the it reaches the Authentication Timeout value or until the user manually locks the application. Control this behavior with the Workspace ONE Intelligent Hub and the SDK profile.
* Challenge Handler and Integrated Authentication
  
  On the Security Policies page, you can set Integrated Authentication to Enabled to allow the SSO credentials or a certificate to be passed on and used for authenticating into Web sites, such as content repositories (SharePoint) or wikis.