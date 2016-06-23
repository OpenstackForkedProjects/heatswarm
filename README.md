Docker Swarm Stack
=========
OpenStack Heat Template to deploy Docker in Swarm mode. By default, provisions
a three node cluster.

`heat stack-create -f dockerswarm.yaml -P public_net_id=<UUID> swarmstack`

Once your stack is up, there will be provisioning time while Docker is
installed. Give it about 10 minutes. Then SSH to the master node and get started
with [Swarm][0].

Parameters
==========
Parameters can be replaced with your own values when standing up a stack. Use
the `-P` flag to specify a custom parameter.

* `docker_node_count`: Number of docker hosts (excluding the master). (Default: 2)
* `public_net_id`: The UUID of your Provider Network in Neutron. Needed for a Floating IP address.
* `instance_flavor`: Flavor of OpenStack Instance to use for Docker (Default: m1.medium)
* `instance_image`: Image to use for the OpenStack Instance. (Default: ubuntu_1404_server_cloudimg_amd64)

Outputs
=======
Once a stack comes online, use `heat output-list <STACKNAME>` to see all available outputs.
Use `heat output-show --format raw <STACKNAME> <OUTPUT>` to get the value of a specific output.

* `docker_ip`: Floating IP
* `ssh_private_key`: SSH Private Key

[0]: https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/
