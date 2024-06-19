---
layout: page
title: Implement the DataSampler
hide:
  #- navigation
  - toc
---

The DataSampler module (formerly known as Interrogator) samples detailed device data and reports it back to the Workspace ONE UEM console.

Device details such as analytics, call logs, GPS location, and network adapters are all sampled with the DataSampler.

!!!Note
 For GPS sampling to function, ensure your application supports location tracking. For more information, see Apple's documentation at https://developer.apple.com/documentation/corelocation.

The DataSampler samples and transmits on two different time intervals. Device samples remain on to the disk and the system removes them after transmitted. This process allows the developer to sample statistics multiple times before sending them to Workspace ONE UEM. Samples stored on the disk are useful when a device does not have network connectivity. AWDataSampler is a singleton object. There can only be one DataSampler for each process.

## Configuration

These parameters are required to set up a DataSampler.
* sampleModules – Names the bit mask whose flags specify which modules to use.
* defaultSampleInterval – Specifies the time in seconds between DataSampler samples for all modules by default.
* defaultTransmitInterval – Specifies the time in seconds between DataSampler transmissions for all modules by default.
* traceLevel – Determines the error and information logging level of the DataSampler module when it is running.

```
[[AWAnalytics mAnalytics] setEnabled:YES];// Initialize DataSampler.   Modify the values in the initializationAWDataSamplerConfiguration *config = [[AWDataSamplerConfiguration alloc] initWithSampleModules:(AWDataSamplerModuleAnalytics | AWDataSamplerModuleGPS) defaultSampleInterval:3600defaultTransmitInterval:14400traceLevel:Error];//This bit mask will enable analytics and GPS sampling  // Configure Data Sampler[[AWDataSampler mDataSamplerModule] setConfig:config]; // Start the Data Sampler Service.NSError *error;[[AWDataSampler mDataSamplerModule] startUp:&error];
```

## Modules Available for Sampling

These modules are available for sampling in the DataSampler.
* AWDataSamplerModuleSystem
* AWDataSamplerModuleAnalytics
* AWDataSamplerModuleGPS
* AWDataSamplerModuleNetworkData
* AWDataSamplerModuleNetworkAdapter
* AWDataSamplerModuleWLAN2Sample

## Gather Telecom Data

Disable the AWDataSamplerModuleNetworkData mask if you gather telecom data using the AirWatch Agent. If you enable this mask for the SDK, then you receive duplicate data from the Agent and from the SDK.

## Set Do Not Disturb

You can use the SDK to set the do-not-disturb (DND) status on the Workspace ONE UEM server. You must enable the DND policy in the Workspace ONE UEM console. You can find the policy at Groups & Settings > All Settings > Devices & Users > General > Privacy > DO NOT DISTURB section.

The two relevant methods are fetchDeviceDNDStatus and setDeviceDNDStatus found in the AWDeviceDNDStatus object. The example illustrates how to implement a toggle button for DND.

```
[AWDeviceDNDStatus fetchDeviceDNDStatus:^(BOOL responseStatus, BOOL dndStatus, NSDate *dndTime, NSError *error){if(dndStatus){[AWDeviceDNDStatus setDeviceDNDStatus:NO completionBlock:^(BOOL responseStatus, BOOL dndStatus, NSDate *dndTime, NSError *error) {NSLog(@"DND Disabled");}];}else{[AWDeviceDNDStatus setDeviceDNDStatus:YES completionBlock:^(BOOL responseStatus, BOOL dndStatus, NSDate *dndTime, NSError *error) {NSLog(@"DND Enabled");}];}}];
```
