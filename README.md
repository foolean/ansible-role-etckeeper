# ansible-role-etckeeper

Ansible role to manage etckeeper


## Requirements

    None


## Dependencies

    None


## Role Variables

    None


## Example playbook

    ```yaml
    ---

    # Ensure that any uncommitted changes in /etc
    # are committed before we start doing anything
    - name: Run etckeeper pre-commit
      hosts: all
      gather_facts: false
      tasks:
        - name: Run etckeeper pre-commit
          ansible.builtin.import_tasks:
            file: "{{ ansible_config_file | dirname }}/roles/foolean/etckeeper/tasks/pre-commit.yml"
          when: not ansible_check_mode


    - name: Playbook
      hosts: all
      roles:
        - foolean/etckeeper


    # Ensure that any uncommitted changes in /etc
    # are committed now that we have finished
    - name: Run etckeeper post-commit
      hosts: all
      gather_facts: false
      tasks:
        - name: Run etckeeper post-commit
          ansible.builtin.import_tasks:
            file: '{{ ansible_config_file | dirname }}/roles/foolean/etckeeper/tasks/post-commit.yml'
          when: not ansible_check_mode

    ```



## License

    BSD-3-Clause
