Jenkins JNLP agent
=========

Minor update: changed some terminology to fit updated urls and terms on jenkins

Install [Jenkins JNLP agent](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds#Distributedbuilds-Launchagentagentheadlessly) on Linux.

Requirements
------------

- Ansible 2.2 or higher.
- Linux with systemd.  
  Tested:
    - Ubuntu
        - 16.04 (xenial)
        - 18.04 (bionic)
    - CentOS
        - 7
- Create user and install Java to run Jenkins on agent machine.
- Create node on Jenkins master.

Role Variables
--------------

- required
  - `jenkins_master`  
  URL of Jenkins server to connect to.
  - `jenkins_agent_secret`  
  Secret key to access Jenkins server as the node.
- defaults
  - `jenkins_agent_user`  
  User to run Jenkins agent. Default value is `jenkins`.
  - `jenkins_agent_group`  
  Group to run Jenkins agent. Default value is `jenkins`.
  - `jenkins_agent_name`  
  Node name of Jenkins agent. Default value is `{{ ansible_hostname }}`.
  - `jenkins_agent_home`  
  Root directory of Jenkins agent. Default value is `/var/lib/jenkins`.
  - `jenkins_agent_java`
  Java binary path. Default value is `/usr/bin/java`.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - { role: paul42.jenkins-jnlp-agent,
             jenkins_master: http://jenkins_master,
             jenkins_agent_secret: secret }
```

License
-------

MIT / BSD

Author Information
------------------

original author is [kobanyan](https://github.com/kobanyan) - updated by [paul42](https://github.com/paul42)
