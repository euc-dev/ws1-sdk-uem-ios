---
layout: page
title: Authentication Type
hide:
  #- navigation
  - toc
---

Authentication Type controls how applications that use the SDK framework to use authenticate to resources. Configure it to work with the SDK default setting for Single Sign-On (SSO) or on its own.

Select an authentication type that meets the security needs of your network. The passcode gives device users flexibility while user name and password offers compatibility with the Workspace ONE UEM system. If security is not an issue, then you do not have to require an authentication type.

| Setting | Description |
| --- | --- |
| Passcode | Designates a local passcode requirement for supported applications. Device users set their passcode on devices at the application level when they first access the application. |
| User name and Password | Requires users to authenticate to supported applications using their Workspace ONE UEM credentials. Set these credentials when you add users in the Accounts page of the Workspace ONE UEM console. |
| Disabled | Requires no authentication to access supported applications.|

## Authentication Type and SSO

Authentication Type and SSO can work together or alone.

* Alone – If you enable an Authentication Type (passcode or user name/password) without SSO, then users must enter a separate passcode or credentials for each individual application.
* Together – If you enable both Authentication Type and SSO, then users enter either their passcode or credentials (whichever you configure as the Authentication Type) once. They do not have to reenter them until the SSO session ends.