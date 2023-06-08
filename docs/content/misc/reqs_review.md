---
title: Requirements Under Review
permalink: reqs_review.html
---

## vTPM Support

- vTPM 2.0 is generated upon creation of a new guest or imported guest without a TPM state file
- Users should be able to create UEFI VMs with vTPMs attached during the VM create process 
- There should be two VM boot types that instantiate a vTPM: UEFI+vTPM and UEFI+vTPM (Compatible) 
    * Both options should be available to all clusters running 9.3 + 
- The two vTPM boot options should configure differences in VM machine types 
    * UEFI+vTPM should create a VM that utilizes a vCPU that is based on the cluster baseline (the Intel generation of the oldest physical CPU in the cluster)
    * UEFI+vTPM (Compatible) should create a VM that utilizes a vCPU of the Intel Haswell generation 
- The vTPM should be emulated in a SCRIBE block device attached to a VM
    * This block device should not be visible in the UI 
    * This block device should be visible via the REST APIs and API clients (like Ansible)
- Users should not be able to delete a vTPM via the UI once attached 
- Users can delete the vTPM block device via REST API call, however this is unrecommended via feature documentation 
- The UI should contain a hint that explains the difference between UEFI+vTPM and UEFI+vTPM (Compatible)
- Our vTPM should accurately emulate TPM 2.0
- The vTPM is visible from within the guest and user can take ownership and return the public key
- vTPM is visible from within the guest and user can store secrets
- vTPM can be used to enable BitLocker in guest 
    * PCR7 is accessible to the guest enabling BitLocker support
- vTPM state and stored values are retained between domain restarts
- vTPM state and stored values are retained after migrating a guest
- vTPM state file remains functional after being backed up and restored
- A VM with both vTPM boot types can successfully run Windows 11
- All SC//Hardware can create VMs with vTPMs 

## SCQAD

Does scqad count as an API client in the edict that "breaking an API client is an API bug and must be fixed/reverted"? Or, is scqad internal test code that might indicate an ambiguous area of the API?


## API v1 
- Is the return value of /rest/v1/Update sorted?
- What values will be returned from this endpoint?
- How should an API user determine which version to update to when multiple are returned?
- Should `VirDomainBlockDeviceCreate` default to tiering `PriorityFactor` or use the value passed in to the API? 

    * **Current behavior:** `use 0` 

[Linked Issue](https://github.lab.local/dev/scaled/issues/440)
