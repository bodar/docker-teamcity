# teamcity
This project can be used to create a Teamcity cluster using docker/docker-machine/docker-compose

How it works:

 * Currently the image expects a existing /data/BuildServer on the host machine or it will default to in-memory DB
 * It supports scaling the agents
 * You have to authorise the agents

What to you might do:

* Provision a bear metal box somewhere with SSH access (or just local)
* Download the standalone binaries for 
  * docker https://github.com/docker/docker/releases/latest
  * docker-machine https://github.com/docker/machine/releases/latest
  * docker-compose https://github.com/docker/compose/releases/latest
* Put them in the path and make them executable
* docker-machine create -d generic --generic-ip-address=${IP} ${fqdn} (or just create a local setup)
* Clone this project
* docker-compose pull
* docker-compose up -d
* docker-compose scale agent 2

If you decide to kill it make sure you do `docker-compose down` otherwise you will get wierd errors about absolute paths 

Future

 * Support restoring from backup zip via environment variable
 * Support downloading JDBC drivers via environment variable





