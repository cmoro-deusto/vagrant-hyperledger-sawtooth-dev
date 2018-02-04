# Vagrant machine for Hyperledger Sawtooth Development

## WARNING: this is a WORK IN PROGRESS

## Requirements
Install vagrant and ansible on your host machine.

## Usage
Clone this repository:
```
$ git clone https://github.com/cmoro-deusto/vagrant-hyperledger-sawtooth-dev.git
$ cd vagrant-hyperledger-sawtooth-dev
```
Bring the vm up:
```
$ vagrant up
```
That will take a while. Once finished, just ssh into the vm:
```
$ vagrant ssh
```
If you got this far, you should have sawtooth example network containers up and running inside the vm. You can check that as follows:
```
$ docker ps
```
You should see several containers running.

## Working with sawtooth
ssh into the vm and launch the `sawtooth-shell.sh` command:
```
$ cd /vagrant
$ ./sawtooth-shell.sh
```
Check that the Sawtooth REST API is running:
```
# curl http://rest-api:8008/blocks
```
You can also access the REST API from within the vagrant vm without starting the sawtooth-shell container:
```
$ curl http://localhost:8008/blocks
```

## Note
The Hyperledger Sawtooth instalation is done following [this guide](https://sawtooth.hyperledger.org/docs/core/releases/latest/app_developers_guide/docker.html). Hyperledger Sawtooth is currently in _active_ development and suffers frequent changes. Provisioning might fail, you have been warned!!
