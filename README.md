# CASino role for Ansible

CASino is a CAS server written in Ruby: http://casino.rbcas.com

The roles will install clone of current master of the CASino app from https://github.com/rbCAS/CASinoApp.git

## Usage

```
- roles:
    - role: casino
      casino_port: "{{ casino_port }}"
      casino_repo: https://github.com/rbCAS/CASinoApp.git
      casino_ldap_host: localhost
      casino_ldap_port: "{{ ldaps_port }}"
      casino_ldap_users_dn: "ou=people,dc=subproject,dc=fi"
      casino_ldap_username_attribute: cn
      casino_ldap_binder_dn: cn=binder,ou=people,dc=subproject,dc=fi
      casino_ldap_binder_password: {{ binder_password }}
```

## Parameters

- casino\_port: port on which the CASinoApp virtualhost listens
- casino\_repo: where to take the CASino app from, defaults to https://github.com/rbCAS/CASinoApp.git
- casino\_ldap\_host: where LDAP backend server is running
- casino\_ldap\_port: on which port is LDAP server listening
- casino\_ldap\_users\_dn: top of the tree with user entries
- casino\_ldap\_username\_attribute: name of the attribute for usernames
- casino\_ldap\_binder\_dn: DN of account under which to bind to LDAP.  Anonymous bind is not supported
- casino\_ldap\_binder\_password: password for binding account

## Notes

The role will install passenger gem and compile passenger module for apache. It will then restart apache with the module. The playbook disables selinux, it's too much of a bother to deal with. If you manage to get a set of selinux rules (the .te file), put it in please.


## Logo
To generate own logo, you can run

```
$ convert -background transparent -fill red -size 128x128  label:"Your\nSSO" files/logo.png
```

