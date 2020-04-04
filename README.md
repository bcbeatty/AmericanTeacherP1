# AmericanTeacherP1
American Teacher Prototype for BuildforCOVID19


### MySQL Database

To setup a local instance of MySQL to run in a docker container and maintain persistent storage, you can do the
following.

Create the following directories on your local . Note that <path to your project docs directory> and <path to your git AT directory> need to be replaced in all commands with the actual paths:
```
mkdir ~/<path to your project docs directory>/at_data/mysql
mkdir ~/<path to your project docs directory>/at_data/mysql/data
mkdir ~/<path to your project docs directory>/at_data/mysql/conf
mkdir ~/<path to your project docs directory>/at_data/mysql/init
```

If it's the first time starting up the database then copy the following file to the init directory. Once the database
is created this DDL file is no longer necessary and can be removed from the init directory. It's only needed there if
you want to create the database from scratch. This will copy all the sql schemas we have and create them locally for you.
```
cp ~/<path to your git AT directory>/docker/sql/*.sql ~/<path to your project docs directory>/at_data/mysql/init
```

To start up the MySQL docker container run the following command
```
docker run --name at-mysql56 -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 -v ~/<path to your project docs directory>/at_data/mysql/conf:/etc/mysql/conf.d -v ~/<path to your project docs directory>/at_data/mysql/data:/var/lib/mysql -v ~/<path to your project docs directory>/at_data/mysql/init:/docker-entrypoint-initdb.d -d mysql:5.6
```

You should now be able to connect to the database on port 3306 (normal port) and login with the username and password

If you are using Mac, you can download SequelPro and connect to the sql running locally, so it's easier to see the tables locally
// TODO add what to use for Windows
