===============================
Cloud.VMware\_Ops Release Notes
===============================

.. contents:: Topics

v1.9.0
======

Minor Changes
-------------

- update community.vmware modules to their vmware.vmware counterparts across the roles and tests

v1.8.0
======

Minor Changes
-------------

- info - added info_datacenters var in documentation to info role
- upload_iso_to_datastore - Created role intended for uploading local ISO files to a Datastore

v1.7.0
======

Minor Changes
-------------

- info - updated role to use vmware.vmware version of module instead of community and vmware_rest versions

v1.6.0
======

Minor Changes
-------------

- Added the option to set environment variables or collection level variables for auth to vcenter. This provides users with a more centralizedoption for setting things that all roles use like vCenter hostname, username, password, etc
- Standardize role README formatting
- cluster_settings - Updated community DPM and DRS recommendation modules to the new vmware.vmware versions
- info - Remove redundant default value for info_validate_certs so the role is consistent with others
- info - added optional output variable which includes gathered info
- info - changed default filenames from randomly generated string to static filename to remove community dependency

Bugfixes
--------

- Made it clearer in the collection README where python requirements are documented
- export_vm_as_ovf - Removed duplicate vars in docs, changed datacenter var name to match other roles while maintaining backwards compat
- fixed typos and grammatical errors in documentation, task names, and changelogs
- manage_folder - Fixed the location of variables in docs to match other roles
- manage_folder - Updated datacenter var name to match other roles while keeping backwards compat

v1.5.1
======

Bugfixes
--------

- removed experiences setup.yml since experiences are not yet supported
- specified support is limited in the README since the collection is meant to be customized by customers

v1.5.0
======

Minor Changes
-------------

- Add variable `provision_vcenter_vm_ntp_server` to handle ntp server
- Added unused var `provision_vcenter_vm_network_ip_family` to template with default value of ipv4
- Fix role names in the README files to be consistent with the ansible-role-template
- Fix the example of guest_os in provision_vm README role to use RHEL guest OS
- Set default value of `time.nist.gov`
- Update the dependencies collections in galaxy.yml and in the execution-environment/requirements.yml
- Update the roles and playbooks in the README in the root directory
- cluster_settings - Use the correct module to apply DRS recommendations instead of cluster module
- cluster_settings - Use the vmware.vmware.cluster module instead of the community.vmware.vmware_cluster module
- cluster_settings - Use the vmware.vmware.cluster_vcls module instead of the community.vmware.vmware_cluster_vcls module
- deploy_ovf - Fixed the pre-check assertions for deploy_ovf_template var since it is required with content libraries and optional otherwise

Bugfixes
--------

- Fixed various typos and spelling issues in the README.md for this repo

v1.4.0
======

Minor Changes
-------------

- cluster_settings - Replaced community.vmware.vmware_cluster_drs module with vmware.vmware.cluster_drs module
- provision_vcenter - Replaced community.vmware.vmware_guest_info module with vmware.vmware.guest_info module
- provision_virtual_esxi - Replaced community.vmware.vmware_guest_info module with vmware.vmware.guest_info module

v1.3.0
======

Minor Changes
-------------

- cluster_settings - add role metadata
- cluster_settings - adding the integration test for cluster settings role
- content_library - add role metadata
- content_library - adding role, playbook, and tests for managing content libraries in a vcenter
- deploy_ovf - add role metadata
- deploy_ovf - added role, playbook, tests for deploying an OVF template to an ESXi or VCenter
- esxi_maintenance_mode - add role metadata
- esxi_maintenance_mode test - adding the integartion test for esxi_maintenance_mode role
- export_vm_as_ovf - add role metadata
- export_vm_as_ovf - added role, playbook, tests to export an existing VM from VCenter or ESXi as an OVF
- export_vm_as_ovf - adding check on ovf file in integration tests for export_vm_as_ovf role
- general change to the testing structure which duplicate runme.sh for each target instead of recreating it manually
- info - add role metadata
- info_test - adding a CI for validated content repo to run on a real vcenter env, and include this test within the pr
- manage_folder - Added new role, tests, and playbook to create or delete a folder in VCenter
- manage_folder - add role metadata
- manage_template - add playbook to manage templates using provision_vm role
- provision_vcenter - add role metadata
- provision_virtual_esxi - add role metadata
- provision_vm - Added parameter to set is_template and defaulted it to false to keep behavior consistent
- provision_vm - add role metadata
- snapshot_management - add role metadata
- system_settings - add role metadata
- vcenter_host_connection - add role metadata
- vcenter_host_connection_test - modified vcenter_host_connection_test to run on a real vcenter environment

Bugfixes
--------

- integration tests - Fixed vsphere automation sdk version in requirements.txt where packages could not properly resolve
- manage_template - Removed playbook because underlying module has a bug and does not support templates

v1.2.0
======

Minor Changes
-------------

- Fix the README file of snapshot_management role to be more clear about the parameters `snapshot_management_folder` and  `snapshot_management_vm_name`
- add_esxi_host_to_vcenter - Added new playbook to add an ESXi host to a vCenter
- cluster_settings - Added new playbook to modify cluster settings
- cluster_settings - Added new role for managing different cluster settings including DRM, DRS, vCLS, HA, and vSAN. Added integration tests for role
- disable_high_availability - Added playbook to disable high availability in  a vcenter cluster
- disable_maintenance_mode - Added new playbook to disable maintenance mode on an ESXi host
- enable_high_availability - Added playbook to enable and configure high availability in a vcenter cluster
- enable_maintenance_mode - Added new playbook to enable maintenance mode on an ESXi host
- esxi_maintenance_mode - Added new role for setting an ESXi host's maintenance mode status. Added integration tests for role
- info - Fix creation of temporary files
- info - Fix the incorrect documentation
- manage_all_settings - Renamed and moved ``cluster_settings.yml`` playbook to ``cluster_settings\manage_all_settings.yml``. New location is with other cluster settings related plays
- provision_vcenter - Only use hdiutil to mount ISO on mac instead of hdiutil + mount. The new approach provides more consistent results when reading the ISO content as a file system
- provision_vcenter - Use OS specific binary when deploying the VCSA appliance (mac vs generic linux) instead of always using linux
- provision_vcenter - When running the playbook on MacOS, the `iso9660` file system is not supported. Instead, Macs need to mount the ISO as a block device and then mount it as `cd9660`. Added new tasks to perform these actions when the os family is darwin
- provision_virtual_esxi - Added new role for provisioning a VM and installing ESXi on it. Added integration tests for role
- reconnect_esxi_host_in_vcenter - Added new playbook to reconnect an ESXi host in a vCenter
- remove_esxi_host_from_vcenter - Added new playbook to remove an ESXi host from a vCenter
- snapshot_management - Add a new role and playbooks to manages virtual machines snapshots in vCenter. (https://github.com/redhat-cop/cloud.vmware_ops/pull/24)
- vcenter_host_connection - Added role to manage the connection status of an ESXI host to a vcenter. Included integration tests for the role

Bugfixes
--------

- esxi_maintenance_mode - Fixed typo in the vmware_maintenancemode module's `evacuate`` attribute
- provision_vcenter - Added dedicated complexity check for VM password at beginning of role. Complexity requirements are normally validated by the VCSA installer but the error thrown can be confusing. Update integration test to use proper password
- provision_vcenter - Changed default ISO mount point from /mnt to /tmp, since /tmp is more likely to be writable
- provision_vcenter - Install libnsl if running on rhel flavored OS, since it is not included in OS version 8+ but needed for the vmware ovftool
- provision_vcenter - Remove leading slashes when a user provides a datacenter/target host path to the installer. These values are supposed to be vcenter folder paths (e.g. /cluster01/host01) but a leading slash would break the VCSA installer config
- provision_vcenter - missing parameters in the validate_inputs tasks. Added them so the user will be alerted sooner if required parameters are missing
- provision_vcenter - the vcsa deploy config was invalid json if dhcp was used. Re-ordered the network section of the config template to fix
- provision_vcenter - vcenter vm names containing a string marked for no_log no longer trigger an unexpected error when checking if the vm already exists
- provision_virtual_esxi - Added missing variable documentation
- provision_virtual_esxi - Role had redundant variable `provision_virtual_esxi_iso_path` that was left from a name refactor. It was updated to match the new name. The new variable name `provision_virtual_esxi_datastore_iso_path` is already mandatory
