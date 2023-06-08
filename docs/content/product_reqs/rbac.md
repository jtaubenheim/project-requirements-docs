---
title: Role-based Access Control (RBAC)
toc: false
permalink: rbac.html
---

I'm adding something here.

## Requirements

- Users will have Roles
- Roles will have permissions
- Multiple Roles will result in a superset of the permissions
- Role permissions are cluster-wide, not per-VM or tag based (yet)
- **No roles = no permissions!**
- Roles must have a unique name in a cluster.
- Permissions will be boolean for each scaled thrift call.
- Reading the permission for a role may hide permissions the role does not have access to
- Once the top level permission has been checked, any further subcalls will not be checked.  For example: If I have clone, but not create permissions, I can still clone a VM, even though scaled must `create` a VM under the hood for the clone.  Reasoning is to allow just this sort of thing.
- In addition to the permissions defined above, there are two additional “special” permissions.  `Read` and `Admin`.  Both are created/updated by the scrolegenerator tool under the hood. The `Admin` role gets every possible permission including many not available to any other role; and the `Read` role gets every possible read permission.  All users get `Read` permissions.  This cannot be removed.
- Users will be able to read their permissions from the session.
- We will add a special update password thrift call. This will allow users to update their password without `UserUpdate` permissions.
- `VirDomainRead` access will give you access to open the console.
- “Local” thrift requests are sessionless, so they won’t be subject to these permissions.  This applies to things like sc tool, other command line tools, and scaled talking to other scaled instances.
- Existing user accounts on clusters will be put into the equivalent of the ‘full administrator’ role by default when upgrading to a version that supports permission levels.
    * Test: `RoleBasedAccessControlUpgradeTest.cpp`
- "Full administrator role" will be a role, just like any other, with all permissions.  This will ship as part of the default configuration.  We will disallow editing any roles via the UI.
- Users can be given more than one role.
- On upgrade, new installations, and cluster reset, a set of predefined roles will be inserted into the cluster configuration.
- User passwords must not be stored in plain text on disk
- Calling `UserUpdate` to change another user’s password should log out any previous sessions owned by the other user
- `UserDelete` should log out any previous sessions owned by the deleted user

