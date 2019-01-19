[Directory Layout]
  # https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#content-organization
  # https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html
  filter_plugins/       # if any custom filter plugins, put them here (optional)
  inventories/
    Dev/
    Prod/
    Staff/
      hosts             # inventory file for Staff PC
      group_vars/
        InfoSec.yml     # here we assign variables to InfoSec groups
      host_vars/
        InfoSecLab.yml  # here we assign variables to InfoSec's Lab systems
    Test/
    UAT/
  library/              # if any custom modules, put them here (optional)
  module_utils/         # if any custom module_utils to support modules, put them here (optional)
  roles/
    InfoSecLab/         # this hierarchy represents a "role"
      defaults/         # default lower priority variables for this role
        main.yml        # When in use, each directory must contain a main.yml file.
      files/            # Contains files which can be deployed via this role.
      handlers/         # Contains handlers, which may be used by this role or even anywhere outside this role.
        main.yml        # handlers file
      library/          # roles can also include custom modules
      lookup_plugins/   # or other types of plugins, like lookup in this case
      meta/             # Defines some meta data for this role. any role dependencies listed therein will be added to the list of roles, subject to tag filtering.
        main.yml        # role dependencies
      module_utils/     # roles can also include custom module_utils
      tasks/            # Contains the main list of tasks to be executed by the role.
        main.yml        # tasks file can include smaller files if warranted
      templates/        # files for use with the template resource
      test/
      vars/             # Other variables for the role.
        main.yml        # variables associated with this role
  README.md
  site.yml              # master playbook
  staff.yml             # playbook for staff tier