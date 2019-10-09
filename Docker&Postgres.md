# Docker
On Ubuntu, Docker can be installed with `apt`:
>sudo apt install docker.io

After installation, in a terminal run (may need sudo):
>docker run -p [port]:5432 postgres

Where [port] is your choice of port. A common port is 5432, a default for many Postgres databases:
>docker run -p 5432:5432 postgres

To run a database as a background process, use the `-d` switch:
>docker run -d -p 5432:5432 postgres

It's a good idea to label a database with the `--name` switch:
>docker run -d --name my_postgres -p 5432:5432 postgres

# Running PostgreSQL with Docker & Dockerfile
To create a custom postgres database, create a file named `Dockerfile`:
```Dockerfile
FROM postgres:10
ENV POSTGRES_USER hello-postgres
ENV POSTGRES_PASSWORD hello-postgres
ADD init.sql /docker-entrypoint-initdb.d
EXPOSE 5432
```

Where init.sql is a `.sql` script file in the same directory as your Dockerfile. Use `ENV` to set the username and password as needed.

To build an image from the Dockerfile:
>docker build -t demo-postgres .

Where `demo-postgres` is the name you wish to give this image. Then to run the build:
>docker run -p 5432:5432 -d demo-postgres

# Connecting to a Docker PostgreSQL database
With your Docker postgres image built and a container running, use `docker exec` to run the `psql` tool on the running container:
>docker exec -it demo-postgres psql -U hello-postgres

Enter your Postgres username after `-U` (`postgres` by default) and enter your password when prompted.