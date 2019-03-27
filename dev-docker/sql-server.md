---
description: Pull and run a SQL Server in Docker
---

# SQL Server

## docker

Pull Image

```text
docker pull mcr.microsoft.com/mssql/server:2017-latest
```

Run Image with port 1433 and volume mount C:\dev\sql

```
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=A123456!" -p 1433:1433 -v C:\dev\sql\data:/var/opt/mssql/data --name sql-dev -d mcr.microsoft.com/mssql/server:2017-latest
```

{% hint style="info" %}
elevated privileges are required
{% endhint %}

Change sa password

```text
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "A123456!" -Q "ALTER LOGIN SA WITH PASSWORD='B123456!'"
```

## docker-compose

use a docker compose file

```yaml
version: "3.7"
services:
  mssql:
    container_name: mssql-dev
    image: mcr.microsoft.com/mssql/server:2017-latest
    volumes: 
      - C:\dev\sql\data:/var/opt/mssql/data
      - C:\dev\sql\backups:/var/backups
    environment:
      - ACCEPT_EULA=Y
      - SA_PASSWORD=A123456!
    ports:
      - 1433:1433

```

## commands

Run sqlcmd in container

* Run bash in container

```
docker exec -it sql-dev "bash"
```

* Run sqlcmd in from bash

```text
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'A123456!'
```

Connect to SQL Server from outside

{% hint style="info" %}
Use the host ip or with the port, for example 192.168.10.206,1433 or localhost,1433 \(the port that was used to run the image\) and the sa login
{% endhint %}



