# Dockerization for Postgres with Northwind Database
This uses *"docker build"* method.  It is based on a standard postgres image for docker hub, and executes *"northwind.sql"* to create a postgres database, calls *"northwind"*.

This build docker image can help developer to quickly setup a database, and to practice sql via *"psql"* or sql commands.

## Quick Start 
To build a basic image
```
docker build -t postgres_northwind:V1.0 -f Dockerfile.Basic ./
```
If docker image is built successfully, below command to run the image to container
```
docker run -d --name mypsql -p 5432:5432 \
  -e POSTGRES_PASSWORD=postgres \
  postgres_northwind:V1.0 
```
Access to **mypsql** container
```
docker exec -ti mypsql bash
docker exec -it mypsql psql -U postgres
```
Then, connect to **psql** command prompt
```
psql -U postgres
```
There should be "northwind" database is created
```
# To list all database(s)
\l
```
To view *"category"* table and content
```
\c northwind

select * from category
```
## PSQL Commands
- [PSQL Cheat Sheet from postgresqltutorial.com](https://www.postgresqltutorial.com/postgresql-cheat-sheet/)
```
\l              # list all databases
\c DB_NAME      # connect to database
\dt             # list all tables
\q              # exit
```