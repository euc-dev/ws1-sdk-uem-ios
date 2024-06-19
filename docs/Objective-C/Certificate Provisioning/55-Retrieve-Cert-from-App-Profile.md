---
layout: page
title: Retrieve a Certificate From an Application Profile
hide:
  #- navigation
  - toc
---

Retrieving certificates requires extra considerations because it involves more than handling a profile. The system stores most profile payloads locally. However, it does not store `AWCertificatePayload` locally. To retrieve the certificate, you must wait for notification that the system downloaded the certificate.

!!!Important: 
   For the SDK to check the server for a certificate, you must call the loadCommands method or the notification does not trigger.

The code below shows how to retrieve a certificate payload so that your application can consume and use the certificate.

```
Register the notification observer at start up.
	[[NSNotificationCenter defaultCenter] 
	addObserver:self

		selector:@selector(handleUpdatedProfile:)

			name:AWNotificationCommandManagerInstalledNewProfile
			object:nil];
```

Implement the `handleUpdatedProfile` that will receive the notifications when a command is processed and can extract the certificate information.

```
- (void)handleUpdatedProfile:(NSNotification 
*)notification
{
// Get the profile that just got received in this call; 
it could be an Application Profile, or an SDK Profile.
 
AWProfile *profile = (AWProfile *)notification.object;
 
// IMPORTANT: If expecting an application profile with a 
certificate, you can ONLY obtain the certificate values 
from the notification object.
 
// For security reasons the certificate does not get 
stored locally, like all the other settings in an SDK 
profile
 
if (profile.certificatePayload){
 
AWCertificatePayload *certificatePayload = 
profile.certificatePayload;
 
if ([[certificatePayload certificateData] length] > 0 & & 
[[certificatePayload certificatePassword] length] > 0)
{
 
	NSString *certificateName = [certificatePayload 
	certificateName]; 
	
	NSData *certificateData = [certificatePayload 
	certificateData]; 

	NSString *certificatePassword = [certificatePayload 
	certificatePassword]; 

	// TO DO: Use the certificate here... If you don't 
	consume it here, it will not be available later in 
	the AWCommandManager.
 
	}
}
```
