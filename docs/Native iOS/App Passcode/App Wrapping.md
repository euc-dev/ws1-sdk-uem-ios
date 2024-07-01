---
layout: page
title: App Wrapping
hide:
  #- navigation
  - toc
---

## Overview

The steps in this tutorial are done with the assumption that you have gone through the steps in [General Setup Tutorial](../index.md) including the wrapping subsection.

## Requirements

- iOS 7+
- Code signing certificate and Provisioning Profile
- iOS Test Device

## Tutorial

### Passcode Policy Configuration

At this point in the tutorial, we assume you have already gone through the steps of uploading your app and assigning the wrapping profile mentioned in [General Setup Tutorial](../index.md).

Log into the AirWatch Console and identify if the wrapping profile you assigned to your application is the default profile or a custom profile.

### Using the Default Profile (Recommended)

1. If the profile assigned is the default profile, then the policy settings can be edited by navigating to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Security Policies.
1. Set Authentication Type to Passcode and configure an appropriate timeout, max number of failed attempts, and passcode complexity.
1. Once you are done, click Save to enforcing the new policy.

### Use an Ad-hoc Custom Profile

1. If the profile assigned is a custom profile you’ve created, then the policy settings can be edited by navigating to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Profiles and then selecting the wrapping profile you’ve assigned to your app.
1. Edit the profile, and select the authentication payload on the left and configure an appropriate timeout, max number of failed attempts, and passcode complexity.
1. Once you are done, click save to start enforcing the new policy.

### Single Sign On

If you choose to enable single sign on in your wrapping profile, then the wrapped app will share the same passcode and authentication session with other wrapped and SDK integrated apps. If enabled, the wrapped application will flip to the AirWatch Agent to broker the authentication instead of presenting the authentication screens within the wrapped app.

### Testing Your Application

1. Enroll your device into AirWatch if you haven’t already done so via the instructions provided in the [General Setup](../index.md) section.
1. Once enrolled, install the wrapped application via your app catalog.
1. Launch the wrapped application and wait for the app to finish initialization.
1. You should be prompted to create a new passcode. (Note: if you enabled Single Sign On, passcode creation will take place in the Agent app instead.)
