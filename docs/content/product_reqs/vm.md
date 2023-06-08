---
title: Virtual Machines (VMs)
permalink: vm.html
toc: false
---

## Requirements

- VMs configured to boot with UEFI must boot
- VMs configured to boot with BIOS must boot
- VMs with 64 bit OSs must boot
- 32 bit OSs may boot
- Hot add and delete on linux vms must work
- GCE VMs configured to boot with UEFI may boot
- Windows VMs configured with UEFI may support hot add and delete
- VM Device expansion 
- VMs must support crash consistent snapshots
- Individual device snapshot must be hot mountable into VMs
- SnapClone VSDs should obtain all first class VSD properties
