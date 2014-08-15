#Automated setup of [hypergraph project](https://github.com/atteroTheGreatest/hypergraph).

This setup will create virtual machine ready for development and interactive exploration.

##Dependencies

- vagrant
- virtualbox
- ansible

##How it works

###Vagrant

Vagrant will pull box image from the internet. Current box is a plain ubuntu 14.04.
Box will be configured in a following way:

 - it will have 2048 MB ram (you can make it smaller - this amount is needed for compilation)
 - it will create a synced folder - syncing data between your host machine and guest
 - create bridged private network, available on http://172.16.0.4/

Vagrant can use various provisioners such as puppet, chef or ansible.
To provision this project I used ansible which is very simple yet powerfull
and well [documented](http://docs.ansible.com/).

After basic machine setup there is an ansible provisioning phase.

###Ansible:

- install basic packages needed for python development
- install packages needed for ipython and matplotlib
- pull the hypergraph sources from github
- create virtualenv and install all python dependencies
- create an upstart job
- start ipython notebook server on private network


##How to use it?

First make sure that you have vagrant, virtualbox and ansible installed
on your machine.

On ubuntu:

```
$ sudo apt-get install virtualbox
$ sudo apt-get install vagrant
$ sudo apt-get install ansible
```

```
$ git clone git@github.com:atteroTheGreatest/hypergraph-provisioning.git
$ cd hypergraph-provisioning && mkdir hypergraph
$ vagrant up
```

and go to http://172.16.0.4:8888/ in your browser. Enjoy :).

You can also ssh to your machine using `vagrant ssh`.
