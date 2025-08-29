**Ansible Notes**

**Source Course: [Getting Started with Ansible: Autimation Made Easy](https://www.udemy.com/course/getting-started-with-ansible/)**

* **ansible all -m gather_facts --limit \<hostname\>** : Gather all ansible facts for requested hosts.

### Running Elevated Commands
* 

## Playbooks
* Remember: yaml format is super particular!
* line to add to .vimrc to make sure tab spaces are yaml compliant
    * **autocmd FileType yaml setlocal ai ts=2 sw=2 et**

## Server Roles
Directory Structure
```
location of playbooks -- > Roles
                            | Role_name
                               |----> tasks (Playbooks specific to this role)
                               |
                               |----> templates (Jinja template files go here)
                               |
                               |----> handlers (taks that can be called by notify in a playbook
                               |
                               |----> files (files to be copied to servers in role)
```

## Register vs Notify
* Notify runs at end
* If you have mutliple notify statements, (i.e.: restarting a service after a config change), if will run only once at the very end as stated above.
* Notify runs handles found in handlers directory

## Templates
* ansible.builtin.template

## Ansible Galaxy
* https://galaxy.ansible.com/ui/
* Check out the roles from geerlingguy!


## Ansible Pull

