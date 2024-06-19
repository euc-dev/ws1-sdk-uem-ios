---
layout: page
title: VMware Workspace ONE SDK Log Levels
hide:
  #- navigation
  - toc
---

Workspace ONE UEM groups logging messages into categories to distinguish critical issues from normal activities.

The Workspace ONE UEM console reports the messages that match the configured logging level plus any logs with a higher critical status. For example, if you set the logging level to Warning, messages with a Warning and Error level display in the Workspace ONE UEM console.

| Level | Logging Syntax | Description |
| --- | --- | --- |
| Error	| AWLogError("{log message}")	| Records only errors. An error displays failures in processes such as a failure to look up UIDs or an unsupported URL. |
| Warning	| AWLogWarning("{log message}")	| Records errors and warnings. A warning displays a possible issue with processes such as bad response codes and invalid token authentications. |
| Information |	AWLogInfo("{log message}") | Records a significant amount of data for informational purposes. An information logging level displays general processes, warning, and error messages. |
| Debug or Verbose | AWLogVerbose("{log message}") | Records all data to help with troubleshooting. This option is not available for all functions.|
