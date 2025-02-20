**Ansible Notes**

**Source Video: [Ansible: From Basics to Guru](https://learning.oreilly.com/videos/ansible-from-basics) by Sander van Vugt** 

####Lesson 1####

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
    * **ansible.builtin.command** : Generic module that allows you to run any command using Ansible
    * **ansible.builtin.shell** : Uses bash shell to run commands, can use shell features like pipes and redirects
    * **ansible.builtin.user** : Manages users
    * **ansible.builtin.copy** : Copies files

* Setting up Managed Hosts
    * Minimal requirements to have a host managed by Ansible
        * SSH running and reachable
        * There is a user with admin privileges.
    * Ad hoc user creation
        * **ansible -i inventory ubuntu24-ansible -m user -a "name=ansible create_home=yes" -u jpreyer -b -k -K**

* Priviledge Escalation
    * Can use -b -K command lin eoptions, but this requires entering a password.
    * use sudo config locally to allow passwordless priviledge escalation, then use ansible copy module to copy the sudo config to managed nodes.

* ansible.cfg
    * Default: /etc/ansible/ansible.cfg (usually), but confirm with **ansible --version**
    * Specific ansible.cfg files can be created in project directories
    * Settings made at a more specific level will always override the generic settings.

###Lesson 2###

* Using Ad-hoc commands
    * Perfect for running one task on a managed host.
    * Perfect for:
        * Initial host setup
        * Checking configurations on hostas
    * Playbooks are used for more complex tasks that have dependency relations.
    * Ansible modules
        * Python scripts that will b executed on managed hosts
        * More than 30000 modules available.
    * Running ad hoc commands
        * run with ansible command
        * when running, inventory must be present and must specify what hosts to address.
        * use -m to address specific module and -a for module args
            * examples: 
                * **ansible -i inventory rocky-hosts -m ansible.builtin.command -a reboot**
                * **ansible -i inventory rocky1 -m ansible.builtin.user -a "name=anna state=present"**
        * in ansible.cfgm you can specify the name of your inventory file undef [defaults] with inventory = \<filename\>
    * Ansible Modules
        * use FQCN when using them (modules are part of Ansible collections since 2.10)
            * example: **ansible.builtin.command** verses **command**
        * Collections allow for better management of large number of modules.
        * List modules with **ansible-doc -l**
        * Essential Ansible Modules
            * **ansible.builtin.command** : runs arbitrary commands on managed nodes, but not through a shell
            * **ansible.builtin.shell** : alternative to **command** and should be used then shell items like pipes and redirects are required.
            * **ansible.builtin.raw** : runs the command without needing Python on node
            * **ansible.builtin.package** : generic module for managing packages
            * **ansible.builtin.user** : allows for user management
        * Best practices
            * Always use the most specific module you can find
            * generic modules often lead to problems in situations where the desired state already exists. (**idempotency**, module should still work as expected is the current state already matched desired state.)
    * Using ansible-doc
        * Module docs is in ansible-doc
        * **ansible-doc -l** will show all modules
        * ansible-doc-modulename gives a details description of the module and its options.
        * **ansible-doc \<module-name\>** will give details on the module
    * **Examples**
        * add user lisa: **ansible all -m user -a "name=lisa state=present"**
        * remove user lisa: **ansible all -m user -a "name=lisa state=absent remove=true"**



