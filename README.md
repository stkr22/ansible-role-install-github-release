Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
        vars:
            github_installs:
            - github_repo_path_part: "docker/compose"
              github_regex_filter: "(?i).*linux-{{ ansible_facts['architecture'] }}$"
              application_install_dir: "/usr/local/lib/docker/cli-plugins/docker-compose"
              use_become: yes
        tasks:
          - name: Install software from github.
            ansible.builtin.include_role:
              name: ansible-role-install-from-github-release
            vars:
              github_repo_path_part: "{{ item.github_repo_path_part }}"
              github_regex_filter: "{{ item.github_regex_filter }}"
              application_install_dir: "{{ item.application_install_dir }}"
              use_become: "{{ item.use_become }}"
            loop: "{{ github_installs }}"
            when: github_installs | length >= 1

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
