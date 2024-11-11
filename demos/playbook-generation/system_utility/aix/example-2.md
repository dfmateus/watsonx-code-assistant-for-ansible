#### **How to access Playbook Generation?**  
Click on the **'Ansible'** icon on VS Code's Activity Bar  
Under **'Ansible Content Creator'** -> **'Get Started'**  
Under **'Create'** -> **'Playbook with Ansible Lightspeed'**

**🎯 Copy the content below and paste into the textarea.**

```yaml
Generate an Ansible playbook to Perform System Image Backup (mksysb) for AIX systems in one workflow, disable facts and them perform the following tasks:
Print a debug message using {{ start_msg }}
Mount NFS share using the ibm.power_aix.mount module with the variables node_v, mount_dir_value and mount_over_dir_value
Backup the rootvg with ibm.power_aix.backup using action create, type mksysb, location var, exclude_files false and extend_fs failed_when false
Assert execution if the previous task was 'succeeded'
Umount NFS share using the ibm.power_aix.mount module with {{ mount_dir_value }} and force
Finally, print a debug message using {{ end_msg }}
```

- Press **"Analyze"** to proceed.
- **Review the suggested steps for your playbook and modify as needed.** _(Prompt refinement)_
- Press **"Generate playbook"** to open a new tab file with the full playbook.

**Note:** _The feature exclusively creates **self-contained** Full Playbooks — it does not generate Ansible roles._
