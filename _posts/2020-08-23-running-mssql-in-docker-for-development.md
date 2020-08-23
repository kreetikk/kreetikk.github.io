---
layout: category-post
title: Running MSSQL Server in docker for development
date: "2020-08-23 11:11:11 -1111"
categories: blog
published: true
---

![MSSQL in docker](/assets/images/docker-post4-cover.png)

Assuming docker and docker-compose are already installed in the machine or else follow the instruction [here](https://docs.docker.com/compose/install/), including the prerequisites.
Create a directory and inside it create a docker-compose.yml file with the following content.

```yaml
version: "3"

services:
  mssql:
    image: mcr.microsoft.com/mssql/server:2019-latest
    volumes:
      - mssql:/var/opt/mssql
    environment:
      - ACCEPT_EULA=Y
      - SA_PASSWORD=yourStrong(!)Password
    ports:
      - "1433:1433"
volumes:
  mssql:
```

Here, we are using docker-compose for simplicity and mssql server 2019 latest image with a volume to persist storage. From the terminal run `docker-compose up` or `docker-compose up -d` for running it in the background. The SQL Server should be up and running.
Now, if you want, you can add a connection and interact with the database in VS Code using extension [SQL Server (mssql)](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).
