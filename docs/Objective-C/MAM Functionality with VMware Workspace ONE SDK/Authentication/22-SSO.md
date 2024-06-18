---
layout: page
title: Single Sign-On and the VMware Workspace ONE SDK for iOS (Objective-C)
hide:
  #- navigation
  - toc
---

To use single sign-on (SSO), an SDK-enabled app must interact with the Workspace ONE Intelligent Hub for handling authentication across multiple apps. After initialization, the app can establish an SSO session with the Workspace ONE Intelligent Hub.

It can delegate the handling of user authentication and SSO management to the Workspace ONE Intelligent Hub or Container. After a session is established in one app, all the other apps can share the session. Applications do not require authentication or passcodes due to this sharing behavior.

The SSO functionality can also allow the application access to the Workspace ONE UEM enrollment credentials for that device if necessary. When the SSO session expires, access to any SSO app requires the user to enter a passcode (depending on the authentication security policies set) and reinitialize the SSO session. The default settings or SDK profile also defines the maximum number of failed attempts. If the user exceeds this number, the session expires and the wipe delegate method invokes in the associated applications to signal the developer to remove local app data.

To implement the SDK, you must implement the code to initialize the SDK using AWController and calling Start from the clientInstance. See the topic Initialize the SDK for more information on initialization. Also, implement the lock, unlock, and wipe methods with the other delegate methods of AWSDKDelegate inside your app delegate.

After you upload the SDK application to the console and assign the a custom or default profile with SSO enabled, the SDK handles communication with the Workspace ONE Intelligent Hub to manage the sessions.

Once the app has finished the communication workflow with the Workspace ONE Intelligent Hub, the app can use the credentials.

Important: To get credentials, devices must enroll using the Workspace ONE Intelligent Hub or Container. Otherwise, the properties are nil.
For information on using Touch ID with the SDK, see the following Workspace ONE UEM Knowledge Base article: https://support.workspaceone.com/articles/115001676428.

## Implementation in Xcode

```
AWEnrollmentAccount *account = [[AWController clientInstance] account];
NSString *username = account.username;
NSString *password = account.password;
NSString *groupID = account.identifier;
```
