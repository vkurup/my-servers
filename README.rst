My Servers
==========


What
----

Automation of services to servers.

Set up
------

1. Create a virtualenv (exercise left to the reader).

#. Install ansible::

     pip install -Ur requirements.txt

#. Install ansible galaxy roles::

     ansible-galaxy install -r requirements.yaml

#. Install vagrant (if you are going to test first)::

     sudo apt install vagrant


Test
----

I use a vagrant box to test these roles::

  vagrant up
  ansible-playbook -l test deploy.yaml
  vagrant destroy


Prod
----

Figure out how you're going to initially connect to the new prod VM (root passwd, key,
etc), and then set those connection variables for the bootstrap play, which will get
your key on there and then turn off root access::

  ansible-playbook -l prod bootstrap.yaml -u root --ask-pass
  ansible-playbook -l prod deploy.yaml


References
----------

* https://www.redhat.com/en/blog/system-administrators-guide-getting-started-ansible-fast
* https://training.play-with-docker.com/docker-networking-hol/
