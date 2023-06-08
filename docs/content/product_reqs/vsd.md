---
title: Virtual Storage Devices (VSDs)
permalink: vsd.html
---

## Requirements

- Live VSD expand must be supported
- Live VSD must not degrade performance
- VSDs must not be able to contract

### VSD Snap Mount

- Mounted snaps must maintain original NTFS security
- Clone/mount and dismount events should be logged in `cluster log` and `syslog`
- Mount events should identify which snapshot was mounted
- Clone/mount events may identify the device by name / timestamp
- User must be able to to correlated disks in OS with scale UI
- Users must have VM Edit User Role to perform SnapClones

### VSD Mount Manages

- Offline VSDs must be deduped
- Offline VSDs must be retiered 

### VSD Upload 

- VSDs must be uploadable via the UI and boot on HC3 if the are in supported formats [TC367 s10-18](https://allure.lab.local/project/1/test-cases/367).
Users must be able to upload the following virtual drive formats: [TC367](https://allure.lab.local/project/1/test-cases/367)
    * .vmdk
    * .qcow2
    * .img
    * .vhd
    * .vhdx
- Users shall be able to upload virtual drives through three methods: 
1. The UI by clicking the `upload` button [TC367 s3-5](https://allure.lab.local/project/1/test-cases/367) in the media menu 
1. The REST APIs [TC391](https://allure.lab.local/project/1/test-cases/391) via curl from any client like insomnia
1. The REST APIs via python or powershell script, and the HyperCore Ansible Collection
- Users should NOT be able to upload virtual drives to the UI by dragging and dropping into the media menu [TC398 s4](https://allure.lab.local/project/1/test-cases/398).

{% include note.html content="This was excluded as a requirement for the original implementation." %}

- Uploaded virtual disks shall be able to be attached to all existing VMs on the HyperCore cluster. [TC367](https://allure.lab.local/project/1/test-cases/367)
- Users should not be able to upload compressed virtual drive files. [TC397](https://allure.lab.local/project/1/test-cases/397)
- Virtual drives do not need to be attached to running VMs 
    * The ability to specify drive type (IDE vs. VIRTIO) was not a requirement for the original implementation 
- There should be a cluster log when a VSD is uploaded and deleted [TC398](https://allure.lab.local/project/1/test-cases/398)
- Uploaded virtual drives shall be correctly listed under the **"Uploaded Virtual Disks”** section in the Media tab of the Control Center [TC367 s8](https://allure.lab.local/project/1/test-cases/367)
- Uploaded virtual drives must show the correct **TOTAL** size [TC367 s13](https://allure.lab.local/project/1/test-cases/367).

{% include note.html content="This often means a drive that is attached to a VM will show a VSD storage capacity larger than the amount of storage actually consumed (allocated). I.e. if a user uploads a 100GB virtual drive that has actually has 10GB worth of data, when attaching to a VM the VSD in HyperCore should reflect 100GB while the guest should report 10GB consumed (allocated)." %}
 
- Uploaded virtual drives should correctly match the **TOTAL** virtual drive capacity once attached to a VM [TC367 s13](https://allure.lab.local/project/1/test-cases/367).
- `Admin` and `Cluster Settings` Roles should be able to upload virtual drives (feature parity with ISO media). The following scaled permissions are used by the VSDUpload endpoint: [rbac.py](https://github.lab.local/dev/scale-qe/blob/cbb9c62f3975e4ea0185bcd184d3761731061415/scqe/rbac.py#L1638)
    * `VSDCreate`
    * `VSDRead`
    * `VSDUpdate`
    * `VSDDelete`
    * `VSDSnapshotCreate`
