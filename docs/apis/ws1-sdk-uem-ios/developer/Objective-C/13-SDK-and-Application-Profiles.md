---
#title: Workspace ONE SDK for iOS
#summary: 
#authors:
    - 
    - 
date: 2024-05-27
#hide:
#  - navigation
#  - toc
---

# SDK and Application Profiles  
The SDK associates with two types of Workspace ONE UEM profiles. These two types are SDK Profiles and application profiles. You assign both types of profiles to the application from the Workspace ONE UEM console.

These profiles are different from Workspace ONE UEM Device Profiles.  
* SDK Profiles – Used to deliver security policies and settings down to the SDK embedded application. Upon receiving an SDK profile, the SDK automatically stores the most recent profile settings in memory.
* Application Profiles – Used to deliver certificates from an upload or a certificate authority down to an application.
   
   Consider using the challenge handler and integrated authentication instead of application profiles.

Polling for Commands and Profile UpdatesThe SDK checks for new commands from Workspace ONE UEM when the app is active in the background. Examples of commands are send logs, update SDK profile, and lock application. However, there may be times when your app wants to check for new commands while active in the foreground. You can do so using the AWCommandManager class with the loadCommands method.
```
// Receive commands.[[AWCommandManager sharedManager] loadCommands];
```
