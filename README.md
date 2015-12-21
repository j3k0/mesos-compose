# Mesos-Compose

Generate docker-compose.yml files for mesos masters or slaves.

## Usage

### Start a master node

Prepare:

	mkdir master-node
	cd master-node

Set the config:

	export INTERFACE=tun0
	export MASTERS="192.168.7.1 192.168.7.2 192.168.7.3"
	export QUORUM="2"

*(alternatively, you can set those lines in a config file in the current directory)*

Generate a configuration file for a master node, in particular the docker-compose.yml and zookeeper config.

Using curl:

	curl -s https://raw.githubusercontent.com/j3k0/mesos-compose/master/compose | bash -s master

Using git:

	git clone https://github.com/j3k0/mesos-compose.git
	./mesos-compose/compose master

You can now find the `docker-compose.yml` file and the `zookeeper` directory that contains persistent data.

Start the master node containers

	docker-compose up -d

Stop the containers, remove, ...

	docker-compose stop
	docker-compose rm

*(See docker-compose own documentation for more commands).*

## Note for larger clusters

The zookeeper ID is set using the IP address' last number. (ex: for `192.168.0.144`, ID is `144`). It's fine if your cluster is small and using a `255.255.255.0`-type netmask, for bigger clusters you can export the `MYID` env to set the zookeeper ID.

## Links

 - [Docker Compose](https://docs.docker.com/compose/)

