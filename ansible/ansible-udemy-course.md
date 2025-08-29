**Ansible Notes**

**Source Course: [Getting Started with Ansible: Autimation Made Easy](https://www.udemy.com/course/getting-started-with-ansible/)**

* **ansible all -m gather_facts --limit \<hostname\>** : Gather all ansible facts for requested hosts.

### Running Elevated Commands
* 

### Playbooks
* Remember: yaml format is super particular!
* line to add to .vimrc to make sure tab spaces are yaml compliant
    * **autocmd FileType yaml setlocal ai ts=2 sw=2 et**

### Server Roles
Directory Structure
location of playbooks -- > Roles --> (role name) --> tasks (Playbooks specific to this role)
                                              |
                                              |
                                               ----> files (files to be copied to servers in role)
