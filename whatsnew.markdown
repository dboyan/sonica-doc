---
layout: page
title: What's New
permalink: /whatsnew/
nav_order: 20
---

# What's New

## Release 3.0 (03/06/2023)

Sonica 3.0 provides the following major updates
* Improving eNodeB MAC layer:
  - The max MCS for uplink and downlink transmissions can be configured;
  - Uplink resource allocation has been improved to support dynamic MCS and number of resource units;
  - Correction on resource allocation timing according to standard;
  - The improvements and fixes allow network benchmark and other applications to work consistently.
* New NB-IoT application: IoT pose recognition and cloud AR reconstruction.
* Various code cleanup and warning fixes.

## Release 2.0 (12/06/2022)

Sonica 2.0 provides the following major updates
* Improvement in eNodeB discovery
  - The time required for initial discovery of Sonica eNodeB reduces from more than 1.5min in release 1.0 to within 15s on tested devices. The discovery time of Sonica is now consistent with the discovery time of commercial NB-IoT networks in the same area.
* Multiple device support:
  - Sonica now supports multiple NB-IoT devices to connect and communicate simultaneously.
* Other misc fixes and improvements in eNodeB and EPC.

## Release 1.0

This is the initial release of Sonica. It supports a single NB-IoT device to connect to the testbed.