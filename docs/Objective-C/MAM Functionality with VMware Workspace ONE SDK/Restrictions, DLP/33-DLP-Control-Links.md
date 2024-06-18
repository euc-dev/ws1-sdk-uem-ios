---
layout: page
title: Use DLP to Control Links to Open in Workspace ONE Web and Workspace ONE Boxer
hide:
  #- navigation
  - toc
---

Configure applications built with the Workspace ONE SDK to open in the Workspace ONE Web and to compose emails in Workspace ONE Boxer. This feature enables end users to use alternative systems other than Safari and the Mail app. To develop this feature, create a bundle in your iOS application and configure Workspace ONE UEM to enforce the behaviors in the bundle.

Configure both systems, the browser and email systems, for this feature to work. Perform the procedures in the listed order.

1. Initial Set Up of the Bundle and PLIST.
   
   For more information, see Initial Set Up of the Bundle and PLIST.

2. Enable Links for Workspace ONE Web.
   
   For more information, see Enable Links for Workspace ONE Web.

3. Enable Links for Workspace ONE Boxer.
   
   For more information, see Enable Links for Workspace ONE Boxer.

4. Contain Data to Workspace ONE Web.
   
   For more information, see Contain Data to Workspace ONE Web.

## Limitation With MFMailComposeViewController

If you use the `MFMailComposeViewController` scheme in your MessageUI framework, this functionality is not supported. The system cannot specify how end users access your application when it is an attachment in an email. End-users access the application with the Mail app and not Inbox.

## SupportInformationController

The SupportInformationController class allows you to query for the email address and telephone numbers for contacting enrollment support which you can display on the application UI.

* [Initial Set Up of the Bundle and PLIST]()
  
  Perform these steps before you enable any links. Use this bundle and PLIST for both HTTP/HTTPS links and MAILTO links.
* [Enable Links for Workspace ONE Web]()
  
  To enable the application to open HTTP / HTTPS links in the Workspace ONE Web, enable a few dictionary and PLIST flags.
* [Enable Links for Workspace ONE Boxer]()
  
  To enable the application to open MAILTO links in Workspace ONE Boxer, enable a few dictionary and PLIST flags.
* [Contain Data to Workspace ONE Web]()
  
  Use the data loss prevention, DLP, settings in the Workspace ONE UEM default SDK profile to enforce the application to use Workspace ONE Web andWorkspace ONE Boxer.
