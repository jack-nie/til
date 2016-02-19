###Install Redis on Centos 6

1. install
```
// --- Compiling ---
$ wget http://download.redis.io/releases/redis-2.8.3.tar.gz
$ tar xzvf redis-2.8.3.tar.gz
$ cd redis-2.8.3
$ make
$ make install

// --- or using yum ---
$ rpm -Uvh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
$ rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

$ yum --enablerepo=remi,remi-test install redis
```
2. config
```
$ sudo nano /etc/sysctl.conf
  vm.overcommit_memory=1
$ sysctl vm.overcommit_memory=1

$ sysctl -w fs.file-max=100000
```
3. Service Commands

```
$ chkconfig --add redis
$ chkconfig --level 345 redis on
$ service redis start/stop/restart
```
