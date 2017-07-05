Universal Tomcat
=========

[![Build Status](https://travis-ci.org/ChristopherDavenport/ansible-role-universal-tomcat.svg?branch=master)](https://travis-ci.org/ChristopherDavenport/ansible-role-universal-tomcat)

This is a system for installing and managing tomcat configurations.

Requirements
------------

None

Role Dependencies
-----------------

[ChristopherDavenport.universal-java](https://galaxy.ansible.com/ChristopherDavenport/universal-java/)  
[ChristopherDavenport.apache-portable-runtime](https://galaxy.ansible.com/ChristopherDavenport/apache-portable-runtime/) - Contingent on `tomcat_use_apr` variable.


Role Variables
--------------

```yaml
# defaults file for universal-tomcat

# Tomcat versions available
# 6.0.47
# 6.0.51
# 7.0.72
# 7.0.76
# 8.0.38
# 8.0.42
# 8.5.6
# 8.5.12
# 9.0.0.M18

tomcat_version: "8.5.12"

tomcat_mirrors:
  - http://archive.apache.org/dist/tomcat

# Temporary Storage Directory
tomcat_tmp_storage: /tmp/tomcat-ansible

# Variable That Decides To Install the APR Role Dependency
tomcat_use_apr: true

tomcat_user_name: tomcat
tomcat_user_group: tomcat
tomcat_user_home: /home/{{ tomcat_user_name }}
tomcat_user_system: false

tomcat_port_shutdown: 8005
tomcat_port_connector: 8080
tomcat_port_redirect: 8443
tomcat_port_ajp: 8009

tomcat_java_opts: ""
tomcat_catalina_opts: ""

tomcat_base_dir: /opt
tomcat_catalina_home: "{{ tomcat_base_dir }}/tomcat"
tomcat_instance_path: "{{ tomcat_base_dir }}/tomcat"

tomcat_prefer_ipv4: true
tomcat_override_uri_encoding: ""
tomcat_prefer_urandom: true

tomcat_instance: tomcat

tomcat_roles:
  - manager
  - manager-gui
  - manager-script
  - manager-jmx
  - admin
  - admin-gui
  - admin-script

tomcat_users: []
  # - name: tomcat
  #   password: tomcat
  #   roles: "manager-gui,admin-gui"
  #

tomcat_debug: false

# This Edits And Allows Ansible To Configure These
# Otherwise it does a default install
tomcat_configure: true
tomcat_configure_configs: "{{ tomcat_configure }}"
tomcat_configure_libs: "{{ tomcat_configure }}"
tomcat_configure_webapps: "{{ tomcat_configure }}"

# These copy files across and will use basename
tomcat_extra_libs_path: []
tomcat_webapps_path: []

# Strings That Allow you to modify your
# tomcat instance in a predictable fashion.
tomcat_extra_global_naming_resources: ""
tomcat_context_xml_header_extra: ""
tomcat_context_xml_extra: ""


# Disable or enable session persistence
tomcat_disable_persistence_across_restarts: false

# Custom Configuration Files
tomcat_use_custom_server_xml: false
# tomcat_custom_server_xml: Path
tomcat_use_custom_web_xml: false
# tomcat_custom_web_xml: Path
tomcat_use_custom_context_xml: false
# tomcat_custom_context_xml: Path
tomcat_use_custom_tomcat_users_xml: false
# tomcat_custom_tomcat_users_xml: Path
tomcat_use_custom_manager_context_xml: false
# tomcat_custom_manager_context_xml: Path

# Tomcat major version
tomcat_version_major: "{{ tomcat_version.0 }}"
tomcat_tar_archive: "apache-tomcat-{{ tomcat_version }}.tar.gz"

tomcat_instance_directories:
  - conf
  - logs
  - webapps
  - temp
  - bin
  - lib
  - work

tomcat_version_specific:
  "6.0.47":
    checksum: md5:7b848f76b605c0fd7fd5c7291a050ca4
    web_xml_schema_version: 3.0
    tomcat_native_version: "1.2.10"
  "6.0.51":
    checksum: md5:c18a8f0cb5966d3f599d49cafeaf7c54
    web_xml_schema_version: 3.0
    tomcat_native_version: "1.2.12"
  "7.0.72":
    checksum: md5:c24bfae15bb9c510451a05582aae634d
    web_xml_schema_version: 3.0
    tomcat_native_version: "1.2.10"
  "7.0.76":
    checksum: md5:ae2e481f918eb2a99a0e47a07e5f1671
    web_xml_schema_version: 3.0
    tomcat_native_version: "1.2.12"
  "8.0.24":
    checksum: md5:9f71353dfba0184c23ecd4743e4132ff
    web_xml_schema_version: 3.1
    tomcat_native_version: "1.2.10"
  "8.0.38":
    checksum: md5:cb1f5e098024df2bb19c581eca180a2a
    web_xml_schema_version: 3.1
    tomcat_native_version: "1.2.12"
  "8.0.42":
    checksum: md5:3cabfc2d3c320b7eb62f8a94da0447ea
    web_xml_schema_version: 3.1
    tomcat_native_version: "1.2.12"
  "8.5.6":
    checksum: md5:e273e27deb1828ae5f19374616b9fba8
    web_xml_schema_version: 3.1
    tomcat_native_version: "1.2.10"
  "8.5.12":
    checksum: md5:c2e6eca5a0642d1e30fbe3573b96ab75
    web_xml_schema_version: 3.1
    tomcat_native_version: "1.2.12"
  "9.0.0.M18":
    checksum: md5:626e16b93de65b2a58714ed50f00d9f9
    web_xml_schema_version: 3.1
    tomcat_native_version: "1.2.12"
```


Dependencies
------------


Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - role: ChristopherDavenport.universal-tomcat
       become: yes
```

License
-------

MIT

Author Information
------------------

This role was created in 2016 by [ChristopherDavenport](https://github.com/ChristopherDavenport).
