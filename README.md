# Box

A server that allows us to test deployments on a VM.

## Dependencies

You'll need Vagrant to prevision a VM. I would recommend als using the Vagrant VMware plugin by HashiCorp.

[https://www.vagrantup.com/vmware/](https://www.vagrantup.com/vmware/)

	$ brew install Caskroom/cask/vagrant

Then follow the instructions from [https://www.vagrantup.com/vmware/](https://www.vagrantup.com/vmware/).

Which are:

	vagrant plugin install vagrant-vmware-fusion

Get the license from your email or whereever and add it.

	vagrant plugin license vagrant-vmware-fusion ~/Downloads/license.lic

## Provisioning a new VM

Download the box and automatically provision.

	$ vagrant up

This will tell you what the IP of the box is during installation. You can always SSH into it using the vagrant CLI.

	$ vagrant ssh
