## vagrant-ansible-asterisk

Ansible script to build an Asterisk server over Vagrant VM, for testing purposes. This repository offers a very simple setup for testing purposes, and should *NOT* be deployed on production environment.

### Install

1. Copy file `sample.settings.yml` to `settings.yml`
2. Edit `settings.yml` with the proper information
3. Launch virtual machine with `vagrant up`

### What each setting means

- boxipaddress: IP address for the server. This should be an IP inside LAN range.
- boxname: Hostname for the server
- interface: Network interface for the server to listen to.
- asterisk\_user: Owner of the Asterisk installation
- asterisk\_group: Group of the Asterisk installation
- asterisk\_ip: IP address to which Asterisk will listen.
- asterisk\_tcp\_port: TCP port to which Asterisk will listen.
- asterisk\_udp\_port: UDP port to which Asterisk will listen.
- asterisk\_tls\_port: Port to which Asterisk will listen when using TLS.
- asterisk\_realm: Realm name for Asterisk instance.
- asterisk\_context: Context name for Asterisk users.
- asterisk\_extension\_tpl: Pattern for extensions configured on dialplan
- asterisk\_users: List of objects, each one corresponding to an Asterisk user:
  - id: Unique identifier for user
  - extension: Unique extension number for user
  - callerid: Call identifier for user
  - secret: Password for user
  - context: Context to which the user is associated

### TODO

- Add MySQL support for configuration, users and so.

