Setting up Mesos using Vagrant
===

This contains two vagrant sandbox environment.

* standalone environment
* multi nodes cluster environment
  * If you prefer to EC2 environment, mesos also ships useful [mesos-ec2 scripts](https://github.com/apache/mesos/blob/master/docs/EC2-Scripts.textile). you can try this also.

The setup is provided by mesos chef cookbook.  Please see [everpeace/cookbook-mesos](http://github.com/everpeace/cookbook-mesos).

Prerequisites
----
* VirtualBox: <https://www.virtualbox.org/>
* vagrant 1.4+: <http://www.vagrantup.com/>
* vagrant plugins
    * [vagrant-omnibus](https://github.com/schisamo/vagrant-omnibus)
          `$ vagrant plugin install vagrant-omnibus`
    * [vagrant-berkshelf](https://github.com/RiotGames/vagrant-berkshelf)
          `$ vagrant plugin install vagrant-berkshelf`
    * [vagrant-hosts](https://github.com/adrienthebo/vagrant-hosts)
          `$ vagrant plugin install vagrant-hosts`
    * [vagrant-cachier](https://github.com/fgrehm/vagrant-cachier)
          `$ vagrant plugin install vagrant-cachier`

Standalone Environment
----
### Setup a Mesos Virtual Box
It's so simple! It's time to get a cup of coffee because this may take some time.

    $ cd standalone
    $ vagrant up

If everything went well, you can see mesos web UI on: <http://localhost:5050>

### Try some example frameworks
please try below by following the [getting started](http://mesos.apache.org/gettingstarted/) document.

    $ vagrant ssh
    vagrant@mesos$ cd /home/vagrant/mesos/build
    vagrant@mesos$ sudo make check
    vagrant@mesos$ src/test-framework --master=zk://mesos:2181/mesos
    vagrant@mesos$ src/examples/java/test-framework zk://mesos:2181/mesos
    vagrant@mesos$ src/examples/python/test-framework zk://mesos:2181/mesos
