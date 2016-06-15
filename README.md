# Cassandra-Cluster-Bootstrap
Ansible Bootstrap for Cassandra Cluster

## Executive summary

This repository provides the ansible scripts to set up a Datastax Cassandra cluster on CentOS servers.

The destination servers have to be setted in inventory file **./inventory.ini**

## Requirements

### Servers
* CentOS 7.x
* Internet gateway

### Ansible gateway
* ansible >= 1.9
* vagrant >= 1.8 (for demo purpose)

## Demo exemple

This repository provides scripts to instanciate a 3-nodes virtualized cluster which runs on 192.168.10.0/24 network.

1. Instanciate the VMs: `vagrant up`
2. Provision the cassandra cluster: `ansible-playbook -i inventory.ini init_cassandra_cluster.yml`
3. Access to cassandra nodes: `ssh ansible@192.168.10.1[1-3]`
3. Destroy the cluster: `vangrant destroy`

## Getting started

To run the cluster initialization scripts on your own machines you have to set up a custom inventory file as follow :

```
[all:vars]
rack=rack1


[cassandra]
hostname-1 ansible_ssh_host=<IP> ansible_connection=ssh datacenter=<DCName> interface_name=<Network_interface>
hostname-2 ...
 ```