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

# Miscellaneous Entries for the Info.PLIST File  
* QR Scan - Include NSCameraUsageDescription in the application info.plist file to enable the SDK to scan QR codes with the device camera.
Provide a description that devices prompt users to allow the application to enable this feature.

* FaceID - Include NSFaceIDUsageDescription in the application info.plist file to enable the SDK to use FaceID.
Provide a description that devices prompt users to allow the application to enable this feature. Consider controlling the message users read. If you do not include a description, the iOS system prompts users with native messages that might not align with the capabilities of the application.