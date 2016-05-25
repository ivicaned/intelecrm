In order to create local development environment do next:

1. Pull this repo

2. Install Docker and Docker Compose

3. docker-machine create
This will create default machine, which is not necessary step.

4. docker-machine create -d virtualbox intelecrm
https://docs.docker.com/machine/get-started/
https://docs.docker.com/machine/reference/create/

5. eval "$(docker-machine env intelecrm)"

6. docker-machine ip default
You will get output like:
192.168.99.101 - remember this ip address we will use it latter


7. Run docker-compose up from root folder, and wait for images to be pulled and
containers to be created

8. Apache server should already listed on port 80, so you can access your website via
http://192.168.99.101/test.php
Changes you make in the source are immediately visible.

9. Now copy sugarcrm code inside crm folder. You can delete test.php file.

10. Open http://192.168.99.101 in browser and start installation.
For Mysql enter next credentials:
host: mysql (yes, host is mysql, it is resolved by docker - check docker-compose.yml)
db: intelecrm
user: intelecrm
pass:intelecrm

root user: root
root password: nikoKaoJa

For Elastic search:
host: elasticsearch (yes, this is host, again check docker-compose.yml)
port: 9200
Note: at this point elastic search on website might show some error,
The key is to reduce number of nodes in elastic search config to 2(this is
what sugarcrm expect), reset elastic search and run building indexes
from sugarcrm admin console.
In future we can build our own docker image, with custom settings for
elastic search based on official one we are using it right now.

11. Complete installation.

If you need to access mysql, you can connect to it using ip address from 6.
At some point we can add phpmyadmin software, but it is not needed for now.

In case you need to access any containers:
docker ps - This will list you all containers with their ids

In command below replace container_id with container id you want to connect
to based on results of previous step
docker exec -i -t container_id /bin/bash






