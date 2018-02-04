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

## Note
The Hyperledger Sawtooth instalation is done following [this guide](https://sawtooth.hyperledger.org/docs/core/releases/latest/app_developers_guide/docker.html). Hyperledger Sawtooth is currently in _active_ development and suffers frequent changes. Provisioning might fail, you have been warned!!
