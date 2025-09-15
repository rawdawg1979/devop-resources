# Ansible Role: wuit-deploy-new-vm
### This is the dev branch for VM Deployment Playbooks
A collection of tasks to deploy a VM template from vCenter
### Collections: 
    vmware.vmware_rest
    community.vmware
    ansible.windows
### Usage:
   Execute the vm_create_new_test.yml against vcenter or import this role and specify the vm_create_new.yml tasks file

```yaml
- ansible.builtin.import_role: wuit-deploy-new-vm
  tasks_from: vm_create_new
``` 
### List of Tasks with required variables and examples:
## 1. vm_create_new
Deploys VM template from vCenter and runs the customization spec which configures the IP address and joins the domain. 
#### Modules:
     vmware.vmware_rest.vcenter_datacenter_info
     vmware.vmware_rest.vcenter_cluster_info
     vmware.vmware_rest.vcenter_datastore_info
     vmware.vmware_rest.vcenter_folder_info
     vmware.vmware_rest.content_locallibrary_info
     vmware.vmware_rest.vcenter_vmtemplate_libraryitems
     vmware.vmware_rest.vcenter_vm_tools_info
     vmware.vmware_rest.vcenter_vm_guest_networking_interfaces_info
     community.vmware.vmware_guest_network
     vmware.vmware_rest.vcenter_vm_power
     vmware.vmware_rest.vcenter_vm_guest_customization
     
 ### vars:
      host_name             : server_name                   < Specify a name for the new virtual machine
      vmware_host           : vc@accounts.wustl.com         < Specify the vcenter server or ESXi host where the vm will be deployed
      vmware_user           : user@wustl.com                < Specify a user with access to fdeploy in vCenter
      vmware_validate_certs : false                         < Select whether or not you weant to validate the SSL certificates (This dhould always be false)
      vmware_password       :                               <
      domain_name           : accounts.washu.com            < Specifies the AD domain this vm will be joined to.
      fqdn                  : hostname@accounts.wustl.com   < Specifies the fully qualified domain of the server ({{ host_name }}.{{ domain_name }})
      os_type               : linux                         < Specifies the type of OS 
      host_ip               : 10.10.10.10                   < Specifies the IP address that will be configured on the vm.
      subnet_mask           : 255.255.255.0                 < Specifies the subnet mask for the selected network
      default_gateway       :                               < Specifies the default gateway for the selected network
      vm_dns_server_1       : 1.2.3.4                       < Specifies the default DNS server
      vm_dns_server_2       : 10.251.22.12                  < Specifies the secondary DNS server
      vm_powered_on         : true                          < Determines whether the VM will be powered on after deployment completes.  Default is true.
      vlan_id               :                               < Specifies the network the VM will be placed on after deployment. 
      vm_template           : vm_template_name              < Specifies the name of the template that will be deployed in vcenter
      vm_folder             : VRA                           < Specifies the name of the folder the VM will be deployed to.
      vm_time_zone          : America/Chicago               < Specifies the time zone