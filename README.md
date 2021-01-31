# Control_repo
## Learning Configuration Management tool

Created a simple minecraft module with the organised code following roles and profiles pattern.

I have setup virtual box running Centos7 managed by vegrance to install and start with Puppet master. 

## Steps to install Vagrant: 
Make sure system has VirtualBox with Virtual media Manager

For Windows, 

Download .msi file from site `https://www.vagrantup.com/` for windos x64.
Install that with standart steps. 

Now we have to setup sanbox. list available at :` https://app.vagrantup.com/boxes/search `

I choose Centos/7. It takes a while to run this command for the first time. (It took half hour on my system)

To create vagrantfile which is configuration file : `vagrant init`

Make sure you ahve admistrative prevelages to run this command.

Vagrantfile has following code:
```
CPUS="1"
MEMORY="1024"

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "master.puppet.vm"

  config.vm.provider "virtualbox" do |v|
    v.name = "master.puppet.vm"
    v.memory = MEMORY
    v.cpus = CPUS
  end

end

```


To start vagrat run : `vagrant up`

To coonect to ssh: `vagrant ssh`

Lets switch to root with: `sudo su -`

default username and password would be : `Vagrant` . But keep public_key in .vagrant folder handy to log in to ssh.

##  Puppetserver Setup

Install puppet from any of the relese at: https://yum.puppetlabs.com/
With command        : `yum install <link to the release>`

I used r10k module to in gem to link my git with server code.

To start server     : `systemctl start puppetserver`

To stop             : `systemctl start puppetserver`

To check status     : `systemctl status puppetserver`

To start my agent   : `puppet agent -p`



