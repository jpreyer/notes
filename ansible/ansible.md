**Ansible Notes**

* Control node is where Ansible software is installed
* Ansible can be installed in differest ways
    * From distro repos (Gives you latest stable software)
    * From Python via pip (Gives you latest, greatest software)
    * For stability, installing from repos is recommended.
* Ansible Requirements
    * Ansible control node
    * python
    * access to ansible playbooks (usually via git)
    * Manged nodes
        * can be Windows, Linux, cloud instances, VM, containers, etc..
        * must have remote access (SSH is default, other platforms use different access)
        * Dedicated user account (Use same user on all nodes)
        * Proviledge escalation to install software, change config files, etc...
    * For convenient management
        * Use ssh keys for passwordless connectins
        * use passwordless proviledge escalation
    * For secure management
        * use -k command line option to prompt for ssh password
        * use -K to prompt for priveledge escalation
    * For convenient and secure management
        * use Ansible Tower, which allows you to cache passwords

* Ansible needs an inventory
    * IDs managed hosts
    * Defines host groups to be used by Ansible
    * Define variables
    * /etc/ansible/hosts is the default inventory
    * -i **inventoryfilename** allowd for project based inventory.

* Ansible ad-hoc commands
    * command line only solution to perform Ansible tasks on managed hosts.
    * Modules can be used in ad-hoc commands to perform tasks
* Modules
    * Since Ansible 2.10, modules are a part of collections
        * a FQCN is used to refer to module names (ex: ansible.builtin.command)
    * In Ansible 2.9 and earlier, only the last part of the name was used.
    


