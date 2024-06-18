---
layout: page
title: SSO Session and the Workspace ONE Intelligent Hub
hide:
  #- navigation
  - toc
---

A single sign-on (SSO) session establishes when a user authenticates with an application participating in in SSO. The session is active until the it reaches the Authentication Timeout value or until the user manually locks the application. Control this behavior with the Workspace ONE Intelligent Hub and the SDK profile.

When using the Workspace ONE Intelligent Hub as a "broker application" for features such as SSO, configure the Workspace ONE Intelligent Hub with the applicable SDK profile. If you are using the default SDK profile, ensure that the Workspace ONE Intelligent Hub is configured to use this profile. If you do not set the Workspace ONE Intelligent Hub to use the default SDK profile, then the system does not apply your configurations you configure in the Settings and Policies section.