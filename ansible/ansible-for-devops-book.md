**Ansible Notes**

## Things to look into
- **pre_tasks / post_tasks**
    - Ansible lets you run tasks before or after the main tasks (defined in tasks:) or roles (defined in roles) using pre_tasks and post_tasks, respectively. 
- **handlers**
    - Handlers are special kinds of tasks you run at the end of a play by adding the notify option to any of the tasks in that group. The handler will only be called if one of the tasks notifying the handler makes a change to the server (and doesn’t fail), and it will only be notified at the end of the play.
