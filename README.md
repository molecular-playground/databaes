# databæs<3

All installation is done automatically through docker. If you do not have docker installed, install [here](https://docs.docker.com/engine/installation/).

### To Run
From inside docker virtual machine, navigate to the top directory of this repository. Enter the following command:
```
docker run --name some-postgres -e POSTGRES_PASSWORD=dankmemes -d postgres
```

### Initialize the database for the first time
To initialize the postgres database for the first time, follow the following steps:
```
# create a postgres container with the corresponding tags
docker run --name some-postgres -e POSTGRES_PASSWORD=dankmemes -d postgres

# copy the init file into the postgres container
docker cp db.sql some-postgres:/home

# begin shell inside of the postgres container
docker exec -i -t some-postgres bash

# navigate to the the init file and initialize the database
$ cd /home
$ psql -f db.sql postgres postgres

# exit the postgres container, you are done!
$ exit
```
Note: Every new container will not have the database initialized. Try ```docker start some-postgres``` to start an old container.
