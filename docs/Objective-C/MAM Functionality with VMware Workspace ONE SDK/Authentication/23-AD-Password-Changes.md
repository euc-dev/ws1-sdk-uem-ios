---
layout: page
title: Active Directory Password Changes
hide:
  #- navigation
  - toc
---

If an Active Directory (AD) password changes and becomes out of sync with the object account of the SDK, use an API to update the SDK credentials.

```
- (void)updateUserCredentialsWithCompletion:(void(^)(BOOL success,NSError *error))completionHandler; 
```

If the callback works, then find the new credentials in the SDK account object.

### Behavior

* SSO disabled – The system displays an authentication prompt within the SDK app for the user to enter in the new credentials.
* SSO enabled – The SDK app flips to the Workspace ONE Intelligent Hub or Container application to update the credentials there. The Workspace ONE Intelligent Hub v5.1+ for iOS and the Container v2.1+ support this behavior.
