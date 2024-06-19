---
layout: page
title: Certificate Provisioning (Legacy Process)
hide:
  #- navigation
  - toc
---

Provisioning certificates to your app involves three steps.

* Configure the certificate authority (CA) and the CA template. Workspace ONE UEM has numerous guides outlining how to configure various certificates. See the applicable guide for information on configuring CAs and CA templates in the Workspace ONE UEM console.
* Create the app profile in the Workspace ONE UEM console.
* Assign the app profile to the application in Workspace ONE UEM prior to app deployment.
* Create the Application Profile
  
  You can create the necessary application profile after you configure the CA and certificate template settings in the Workspace ONE UEM console. This profile is deployed to the app just like an SDK profile.
* Retrieve a Certificate From an Application Profile
  
  Retrieving certificates requires extra considerations because it involves more than handling a profile. The system stores most profile payloads locally. However, it does not store AWCertificatePayload locally. To retrieve the certificate, you must wait for notification that the system downloaded the certificate.
