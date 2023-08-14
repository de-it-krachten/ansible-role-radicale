[![CI](https://github.com/de-it-krachten/ansible-role-radicale/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-radicale/actions?query=workflow%3ACI)


# ansible-role-radicale

Installs & configues radicale<br>
Free and Open-Source CalDAV and CardDAV Server<br>
https://radicale.org<br>



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 10 (Buster)<sup>1</sup>
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 37
- Fedora 38

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Version of radicale to install
radicale_version: latest

# Radicale user / group
radicale_user: radicale
radicale_group: radicale

# Radicale collections location
radicale_collections_dir: /var/lib/radicale/collections

# Logging directory
radicale_log_dir: /var/log/radicale

# basic configuration
radicale_default_config:
  auth:
    type: htpasswd
    htpasswd_filename: /etc/radicale/users
    htpasswd_encryption: bcrypt
    delay: 5
  server:
    hosts: "127.0.0.1:5232"
  logging:
    level: warning
    mask_passwords: true
  storage:
    filesystem_folder: "{{ radicale_collections_dir }}"
  web:
    type: none

# List of python/pip packages
radicale_pip_packages:
  - passlib
  - "bcrypt>3,<4"
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'radicale'
  hosts: all
  become: "yes"
  tasks:
    - name: Include role 'radicale'
      ansible.builtin.include_role:
        name: radicale
</pre></code>
