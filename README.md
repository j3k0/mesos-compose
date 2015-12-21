# Mesos-Compose

Generate docker-compose.yml files for mesos masters or slaves.

## Usage

Prepare:

	git clone https://github.com/j3k0/mesos-compose.git
	mkdir master-node
	cd master-node

Set the config:

    INTERFACE=tun0
	MASTERS="192.168.7.1 192.168.7.1 192.168.7.1"
	QUORUM="2"

*(alternatively, you can set those lines in a config file in the current directory)*

Generate a docker-compose.yml file for a master node

	../mesos-compose/mesos_master

Start the master node containers

	docker-compose up -d

Stop the containers, remove, ...

	docker-compose stop
	docker-compose rm

*(See docker-compose own documentation for more).*

## Links

 - [Docker Compose](https://docs.docker.com/compose/)

