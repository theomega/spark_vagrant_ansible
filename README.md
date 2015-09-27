# spark_vagrant_ansible
Try out Spark 1.5 out using VMs provisioned by Vagrant and Ansible 

## What is this
This reopsitory provides a [Vagrant][1] file which installs in combination with an [Ansible][2] playbook:

- Ubuntu 14.04
- Spark 1.5 (and its dependencies)

## How to use

1. Install the following dependendencies on your machine:

- Vagrant
- ansible
- vagrant-ansible

2. Clone the repository
3. Launch the machines:
- `vagrant up spark-master`
- `vagrant up spark-slave1`
- `vagrant up spark-slave2`

4. Check the Spark Webinterface at http://192.168.33.10:8080/


  [1]: https://www.vagrantup.com/
  [2]: http://www.ansible.com/
  
5. To launch a spark job, use the `/opt/spark/bin/spark-submit-local` script on the spark-master vm. Connect to this machine using `vagrant ssh spark-master`
  
## Limitations:

- Spark runs in stand alone more, this means that there is no underlying hadoop or HDFS. If you need to work on files, you need to have them shared on all machines. The `/data` folder is shared between all machines and also the host. You can put files there and use them.
- As all VMs run on your computer, memory is any issue. The ansible playbook configures spark quite memory constrainted. You can change these limits by first giving the VMs more memory (in the `Vagrantfile`) and then changing the launchers in the `rules/spark-master` and `rules/spark-slave` folder
