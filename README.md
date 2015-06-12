<!--

---
lang: american
---
-->

[![Build Status](https://travis-ci.org/cw-ansible/cw.ansible-bootstrap.svg?branch=master)](https://travis-ci.org/cw-ansible/cw.ansible-bootstrap)
[![Tweet this](http://img.shields.io/badge/_-Tweet-00aced.svg)](https://twitter.com/intent/tweet?tw_p=tweetbutton&via=renard_0&url=https%3A%2F%2Fgithub.com%2Fcw-ansible%2Fcw.ansible-bootstrap&text=Create%20an%20%23ansible%20user%20and%20configure%20its%20credentials)
[![Follow me on twitter](http://img.shields.io/badge/Twitter-Follow-00aced.svg)](https://twitter.com/intent/follow?region=follow_link&screen_name=renard_0&tw_p=followbutton)


# Bootstrap ansible

Create an ansible user and configure its credentials

## Usage

Include the `cw.ansible-bootstrap` module to your playbook.

If you use this role for the very first time on a remote system you need a
`root` or `sudo` access to remote host and you need to run it using
following command:

	ansible-playbook -l HOST -K pb_ansible-bootstrap.yml -e user=USER

If you want to bootstrap `localhost` just run:

	ansible-playbook -l localhost -K  pb_ansible-bootstrap.yml

or:

	ansible-playbook -l localhost -c local -K pb_ansible-bootstrap.yml


The content of `pb_ansible-bootstrap.yml` is something similar to:

    - hosts: "all"
      user: '{{ user | default("ansible")}}'
      sudo: yes
      sudo_user: root
    
      roles:
        - { role: cw.ansible-bootstrap, tag: cw.ansible-bootstrap }


## Description

This roles creates an `ansible` user on the system and configure all
credentials for a password-less and a root-less access.


## Configuration

See specific documentation in `defaults/main.yml`



## Copyright

Author: Sébastien Gross `<seb•ɑƬ•chezwam•ɖɵʈ•org>` [@renard_0](https://twitter.com/renard_0)

License: WTFPL, grab your copy here: http://www.wtfpl.net
