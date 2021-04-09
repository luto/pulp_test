# pulp test

```console
$ ansible --version
ansible 2.10.7
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/luto/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3.9/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.9.2 (default, Feb 20 2021, 18:40:11) [GCC 10.2.0]
$ rm -rf ~/.ansible/
$ ansible-galaxy install geerlingguy.postgresql
Starting galaxy role install process
- downloading role 'postgresql', owned by geerlingguy
- downloading role from https://github.com/geerlingguy/ansible-role-postgresql/archive/3.1.0.tar.gz
- extracting geerlingguy.postgresql to /home/luto/.ansible/roles/geerlingguy.postgresql
- geerlingguy.postgresql (3.1.0) was installed successfully
$ ansible-galaxy collection install pulp.pulp_installer
Starting galaxy collection install process
Process install dependency map
Starting collection install process
Installing 'pulp.pulp_installer:3.11.0' to '/home/luto/.ansible/collections/ansible_collections/pulp/pulp_installer'
Downloading https://galaxy.ansible.com/download/pulp-pulp_installer-3.11.0.tar.gz to /home/luto/.ansible/tmp/ansible-local-897651uz42uqka/tmpytap8rss
pulp.pulp_installer (3.11.0) was installed successfully
Installing 'ansible.posix:1.2.0' to '/home/luto/.ansible/collections/ansible_collections/ansible/posix'
Downloading https://galaxy.ansible.com/download/ansible-posix-1.2.0.tar.gz to /home/luto/.ansible/tmp/ansible-local-897651uz42uqka/tmpytap8rss
ansible.posix (1.2.0) was installed successfully
$ vagrant provision
==> default: Running provisioner: ansible...
    default: Running ansible-playbook...
[DEPRECATION WARNING]: The use of 'static' has been deprecated. Use 
'import_tasks' for static inclusion, or 'include_tasks' for dynamic inclusion. 
This feature will be removed from ansible-base in version 2.12. Deprecation 
warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.

PLAY [all] *********************************************************************

TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Load OS specific variables] **********
ok: [default]

TASK [pulp.pulp_installer.pulp_database : include_tasks] ***********************
included: /home/luto/.ansible/collections/ansible_collections/pulp/pulp_installer/roles/pulp_database/tasks/install_postgres.yml for default

TASK [pulp.pulp_installer.pulp_database : Check if PostgreSQL < 10 is initialized.] ***
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Get PG_VERSION] **********************
skipping: [default]

TASK [pulp.pulp_installer.pulp_database : Stop PostgreSQL < 10 service] ********
skipping: [default]

TASK [pulp.pulp_installer.pulp_database : Install SCL package] *****************
changed: [default]

TASK [pulp.pulp_installer.pulp_database : Install PostgreSQL SCL] **************
changed: [default]

TASK [pulp.pulp_installer.pulp_database : Enable PostgreSQL SCL] ***************
changed: [default]

TASK [pulp.pulp_installer.pulp_database : Backup previous PostgreSQL] **********
skipping: [default]

TASK [pulp.pulp_installer.pulp_database : Check if PostgreSQL database is initialized.] ***
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Upgrade to PostgreSQL 10] ************
skipping: [default]

TASK [pulp.pulp_installer.pulp_database : Check if PostgreSQL database is initialized.] ***
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Ensure PostgreSQL database is initialized.] ***
[WARNING]: Module remote_tmp /var/lib/pgsql/.ansible/tmp did not exist and was
created with a mode of 0700, this may cause issues when running as another
user. To avoid this, create the remote_tmp dir with the correct permissions
manually
changed: [default]

TASK [pulp.pulp_installer.pulp_database : Get PATH] ****************************
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Set PATH as a fact] ******************
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Get LD_LIBRARY_PATH] *****************
ok: [default]

TASK [pulp.pulp_installer.pulp_database : Set LD_LIBRARY_PATH as a fact] *******
ok: [default]

TASK [Install and configure PostgreSQL] ****************************************

TASK [geerlingguy.postgresql : include_tasks] **********************************
included: /home/luto/.ansible/roles/geerlingguy.postgresql/tasks/variables.yml for default

TASK [geerlingguy.postgresql : Include OS-specific variables (Debian).] ********
skipping: [default]

TASK [geerlingguy.postgresql : Include OS-specific variables (RedHat).] ********
ok: [default]

TASK [geerlingguy.postgresql : Include OS-specific variables (Fedora).] ********
skipping: [default]

TASK [geerlingguy.postgresql : Define postgresql_packages.] ********************
skipping: [default]

TASK [geerlingguy.postgresql : Define postgresql_version.] *********************
ok: [default]

TASK [geerlingguy.postgresql : Define postgresql_daemon.] **********************
skipping: [default]

TASK [geerlingguy.postgresql : Define postgresql_data_dir.] ********************
skipping: [default]

TASK [geerlingguy.postgresql : Define postgresql_bin_path.] ********************
skipping: [default]

TASK [geerlingguy.postgresql : Define postgresql_config_path.] *****************
skipping: [default]

TASK [geerlingguy.postgresql : Define postgresql_unix_socket_directories_mode.] ***
ok: [default]

TASK [geerlingguy.postgresql : include_tasks] **********************************
included: /home/luto/.ansible/roles/geerlingguy.postgresql/tasks/setup-RedHat.yml for default

TASK [geerlingguy.postgresql : Ensure PostgreSQL packages are installed.] ******
ok: [default]

TASK [geerlingguy.postgresql : Ensure PostgreSQL Python libraries are installed.] ***
changed: [default]

TASK [geerlingguy.postgresql : include_tasks] **********************************
skipping: [default]

TASK [geerlingguy.postgresql : include_tasks] **********************************
included: /home/luto/.ansible/roles/geerlingguy.postgresql/tasks/initialize.yml for default

TASK [geerlingguy.postgresql : Set PostgreSQL environment variables.] **********
changed: [default]

TASK [geerlingguy.postgresql : Ensure PostgreSQL data directory exists.] *******
ok: [default]

TASK [geerlingguy.postgresql : Check if PostgreSQL database is initialized.] ***
ok: [default]

TASK [geerlingguy.postgresql : Ensure PostgreSQL database is initialized.] *****
skipping: [default]

TASK [geerlingguy.postgresql : include_tasks] **********************************
included: /home/luto/.ansible/roles/geerlingguy.postgresql/tasks/configure.yml for default

TASK [geerlingguy.postgresql : Configure global settings.] *********************
changed: [default] => (item={'option': 'unix_socket_directories', 'value': '/var/run/postgresql'})

TASK [geerlingguy.postgresql : Configure host based authentication (if entries are configured).] ***
changed: [default]

TASK [geerlingguy.postgresql : Ensure PostgreSQL unix socket dirs exist.] ******
changed: [default] => (item=/var/run/postgresql)

TASK [geerlingguy.postgresql : Ensure PostgreSQL is started and enabled on boot.] ***
changed: [default]

TASK [geerlingguy.postgresql : Ensure PostgreSQL users are present.] ***********
changed: [default] => (item={'name': 'pulp', 'password': 'pulp', 'role_attr_flags': 'CREATEDB'})

TASK [geerlingguy.postgresql : Ensure PostgreSQL databases are present.] *******
changed: [default] => (item={'name': 'pulp', 'owner': 'pulp'})

TASK [geerlingguy.postgresql : Ensure PostgreSQL users are configured correctly.] ***
changed: [default] => (item={'name': 'pulp', 'password': 'pulp', 'role_attr_flags': 'CREATEDB'})

TASK [pulp.pulp_installer.pulp_redis : Load OS specific variables] *************
ok: [default]

TASK [pulp.pulp_installer.pulp_redis : Install Redis] **************************
fatal: [default]: FAILED! => {"changed": false, "msg": "No package matching 'redis' found available, installed or updated", "rc": 126, "results": ["No package matching 'redis' found available, installed or updated"]}

RUNNING HANDLER [geerlingguy.postgresql : restart postgresql] ******************

PLAY RECAP *********************************************************************
default                    : ok=34   changed=13   unreachable=0    failed=1    skipped=13   rescued=0    ignored=0   

Ansible failed to complete successfully. Any error output should be
visible above. Please fix these errors and try again.
```
