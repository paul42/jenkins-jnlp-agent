Jenkins JNLP Slave
=========

Install [Jenkins JNLP slave](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds#Distributedbuilds-Launchslaveagentheadlessly) on Ubuntu.

Requirements
------------

Create user and install Java to run Jenkins.

Role Variables
--------------

- required
  - `jenkins_master`  
  URL of Jenkins server to connect to.
  - `jenkins_slave_secret`  
  Secret key to access Jenkins server.
- defaults
  - `jenkins_slave_user`  
  User to run Jenkins slave. Default value is `jenkins`.
  - `jenkins_slave_group`  
  Group to run Jenkins slave. Default value is `jenkins`.
  - `jenkins_slave_name`  
  Node name of Jenkins slave. Default value is `{{ ansible_hostname }}`.
  - `jenkins_slave_home`  
  Root directory of Jenkins slave. Default value is `/var/lib/jenkins`.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - { role: kobanyan.jenkins-jnlp-slave,
             jenkins_master: http://jenkins_master,
             jenkins_slave_secret: secret }
```

License
-------

MIT / BSD

Author Information
------------------

[kobanyan](https://github.com/kobanyan)