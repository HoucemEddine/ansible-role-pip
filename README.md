# Ansible Role: Pip (for Python)

This is forked from https://github.com/geerlingguy/ansible-role-pip
[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-pip.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-pip)

An Ansible Role that installs [Pip](https://pip.pypa.io) on Linux.

## Requirements

On RedHat/CentOS, you may need to have EPEL installed before running this role. You can use the `geerlingguy.repo-epel` role if you need a simple way to ensure it's installed.

## Role Variables

The role will install python 2 or python 3 packages using pip or pip3 acconrdingly

    pip_2_packages: []
    pip_3_packages: []
A list of packages to install with pip. Examples below:

    pip_2_packages:
      # Specify names and versions.
      - name: docker
        version: "1.2.3"
      - name: awscli
        version: "1.11.91"
    
      # Or specify bare packages to get the latest release.
      - docker
      - awscli
    
      # Or uninstall a package.
      - name: docker
        state: absent
    
      # Or update a package ot the latest version.
      - name: docker
        state: latest
    
      # Or force a reinstall.
      - name: docker
        state: forcereinstall
    
      # Or install a package in a particular virtualenv.
      - name: docker
        virtualenv: /my_app/venv

## Dependencies

None.

## Example Playbook

    - hosts: all
    
      vars:
        pip_2_packages:
          - name: ansible
          - name: awscli
        
        pip_3_packages:
          - name: awscli
          - 
      roles:
        - HoucemEddine.pip

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
