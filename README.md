MTN.*NIX.11 Automated Environment Configuration Management
---

***Student***: [Uladzislau Charches](https://upsa.epam.com/workload/employeeView.do?employeeId=4060741400038705754#emplTab=general)

# Puppet lesson_13

**Task1**

**1. I edited 2 Vagrantfiles. Run it with edited files "host" on client VM. You can check it below**

[Vagrantfile-client](https://github.com/VladCharches/lesson13/blob/master/Vagrant_Client)
[Vagrantfile-server](https://github.com/VladCharches/lesson13/blob/master/Vagrantfile_server)

**Server-side (All operations we should do on root)** 

I installed theforeman

$ yum -y install epel-release https://yum.theforeman.org/releases/1.12/el6/x86_64/foreman-release.rpm

$ yum -y install foreman-installer

$ foreman-installer

# I recieved a problem with names server and client and i rename it to pserv and node1

**Client-side:**

puppet agent --server pserv.minsk.epam.com -t

# I created folders and new manifest, 
$ mkdir /etc/puppetlabs/code/environments/prod
$ mkdir /etc/puppetlabs/code/environments/prod/manifests

# I created manifest $ vi /etc/puppetlabs/code/environments/prod/manifests/site.pp

# My manifest [site.pp](https://github.com/VladCharches/lesson13/blob/master/site.pp) 

# Installed module mysql
$ puppet module install puppetlabs-mysql --environment prod

Also edited and add new environment 'prod' $ vi /etc/puppetlabs/puppet/[puppet.conf](https://github.com/VladCharches/lesson13/blob/master/puppet.conf) 


**Client-side:**

puppet agent --server pserv.minsk.epam.com -t --environment prod |tee /vagrant/outlog.log

[output.log](https://github.com/VladCharches/lesson13/blob/master/outlog.log)

Screenshots:

**Results**

![1](https://github.com/VladCharches/lesson13/blob/master/Screens/1.png)
![2](https://github.com/VladCharches/lesson13/blob/master/Screens/2.png)
![3](https://github.com/VladCharches/lesson13/blob/master/Screens/3.png)
