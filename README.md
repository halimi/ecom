# ecom

E-commerce REST API in Go using JWT authentication.

## Setup

### Database

This project is using MySQL database. You can use `docker` to run it.

```bash
$ docker run --name mysql-ecom -e MYSQL_ROOT_PASSWORD=my-secret-pw -p 3306:3306 -d mysql:9
```
*Don't forget to change the password!*

You need to create the database, the default name is 'ecom'.

To able to do that you need to get a shell in the running container.

```bash
$ docker exec -it mysql-ecom bash
```

In this shell you need to open a `mysql` shell and create the database.

```bash
$ mysql -p

mysql> create database ecom;

mysql> exit

$ exit
```

### Database migration

For the database migration you need to install the `golang-migrate` tool.

```bash
$ go install -tags 'mysql' github.com/golang-migrate/migrate/v4/cmd/migrate@latest
```

After this you need to run the migrations.

```bash
$ make migrate-up
```

## Running the project

If you have a running MySQL database and you ran the migrations then you can run the project with the following command:

```bash
$ make run
```
