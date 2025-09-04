**Ansible Notes**

## Things to look into
- **pre_tasks / post_tasks**
    - Ansible lets you run tasks before or after the main tasks (defined in tasks:) or roles (defined in roles) using pre_tasks and post_tasks, respectively. 
- **handlers**
    - Handlers are special kinds of tasks you run at the end of a play by adding the notify option to any of the tasks in that group. The handler will only be called if one of the tasks notifying the handler makes a change to the server (and doesn’t fail), and it will only be notified at the end of the play.
- **templates**
- **commands module**
    - See https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html for more info
    - In particular, how does creates and removes parameters work
- The command module is preferred over shell command, use shell when you need to pipe/redirect input|output to/from a command you are running.
- **ansible.builtin.stat** - retrieve file status (https://docs.ansible.com/ansible/latest/collections/ansible/builtin/stat_module.html)
- Look at installing Solr in chapter 4, good example to follow
