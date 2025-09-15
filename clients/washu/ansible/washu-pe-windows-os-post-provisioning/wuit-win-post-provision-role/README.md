# Ansible Role: dto_dcops_win_postprov
This is the dev branch for Windows Post Provisioning Playbooks

## Collections:
    ansible.windows

## Usage:
Execute the desired task file in the tasks directory of this repository by using the ```include_role``` module and utilizing the ```task_from``` property from that role.

---

## Lists of Tasks with required variables and examples:
1. **rsa_install**

Fetches the installation file for RSA from a remote file share.

**NOTE**: Currently, the RSA installer is being fetched from a remote share in Techlab. In the future, this file will be pulled from Artifactory.

Vars:

    N/A

---

2. **splunk_update**

Runs the POSH script which updates Splunk for the newly provisioned VM.

Vars:

    N/A

---

3. **update_registry**

Runs the POSH script which updates the registry on the newly provisioned Windows VM.

Vars:

    bpName              : Blueprint -- test             < vsphere blueprint that the VM was provisioned with 
    classification      : dev                           < dev, prod, QA, etc
    vmOwner             : Jamison                       < Who requested the VM
    cloneTemplate       : 2019DCVRATemplateD2021Jan08   < Template the VM was provisioned from
    notes               : test                          < Some notes about the VM
---
