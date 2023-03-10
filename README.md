Ansible Role: Kadalu Install
=========

Install and configure the Kadalu project

Requirements
------------

Kubernetes and unused physical volumes to place in the Kadalu storage pool.

Role Variables
--------------

The following variables are defined in the defaults/main.yml file:

    # Version to install
    kadalu_version: "1.0.0"

    # Name for the storage pool to create
    storage_pool_name: "storage-pool-neb"

    # type = Replica[1,2,3], Disperse
    kadalu_pool_type: Replica3

Dependencies
------------

None.

Example Playbook
----------------

    # ===========================================================================
    # Install Kadalu and optional demo application
    # ===========================================================================

    - name: Install Kadalu
      hosts: k8s_master
      tags: play_kadalu_install
      gather_facts: true

      vars_files:
        # Ansible vault with all required passwords
        - "/home/apatt/github/demopod-ansible/credentials.yml"

      roles:
        - { role: ansible-role-kadalu, npod_name: "K8s_Lenovo" }

License
-------

MIT

Author Information
------------------

Aaron Patten
aaronpatten@gmail.com
