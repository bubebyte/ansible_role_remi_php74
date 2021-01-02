# remi_php74

## Description
Ansible role to install and configure php74 from remi repository.

## Example Playbook
```YAML
---
- name: PHP
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: bubebyte.remi_php74
```

## Role Variables
These are the role default which are set in default/main.yml:
```YAML
---
remi_php74_install_epel_repository: true
remi_php74_install_remi_repository: true
remi_php74_extra_packages: []
remi_php74_fpm_enable: true
remi_php74_fpm_pools:
  - name: www
    options:
      user: apache
      group: apache
      listen: /var/opt/remi/php74/run/php-fpm/www.sock
      listen.mode: "0660"
      listen.acl_users: apache
      listen.allowed_clients: 127.0.0.1
      pm: dynamic
      pm.max_children: 50
      pm.start_servers: 5
      pm.min_spare_servers: 5
      pm.max_spare_servers: 35
      slowlog: "/var/opt/remi/php74/log/php-fpm/www-slow.log"
      php_admin_value[error_log]: "/var/opt/remi/php74/log/php-fpm/www-error.log"
      php_admin_flag[log_errors]: "on"
      php_value[session.save_handler]: files
      php_value[session.save_path]: /var/opt/remi/php74/lib/php/session
      php_value[soap.wsdl_cache_dir]: /var/opt/remi/php74/lib/php/wsdlcache
```

## Requirements

### Roles
none

### Collections
- community.general

## License
MIT License

## Author Information
[Armin Bube](https://bubebyte.de)
