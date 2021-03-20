# Kernel modules

[Blog post][blog] covering some of the setup for a hello.c example

## Working environment

In this repo you should be able to get running with:
1. `git clone https://github.com/KlotzAndrew/kernel-modules.git`
1. `cd kernel-modules`
1. `vagrant up`
1. `vagrant ssh`
1. `cd src`

This will drop you into a vagrant shell with file sync to your current directory

### Installing Vagrant

Skip if you already have Vagrant installed

```bash
apt install virtualbox

curl -SL --progress-bar https://releases.hashicorp.com/vagrant/2.2.14/vagrant_2.2.14_linux_amd64.zip --output /tmp/vagrant.zip
unzip -o /tmp/vagrant.zip -d /usr/local/bin
rm  /tmp/vagrant.zip

# libarchive-tools not default in ubuntu 20.04
apt-get install libarchive-tools

vagrant --version

vagrant plugin install vagrant-vbguest
```

### Compiling and Running

There is first time setup for installing your kernel headers
```bash
make setup
```

Compiling
```bash
make all
```

Running
```bash
sudo /sbin/insmod hello.ko
sudo /sbin/rmmod hello.ko

tail /var/log/kern.log
```

[blog]: https://klotzandrew.com/blog/making-your-first-linux-kernel-module
