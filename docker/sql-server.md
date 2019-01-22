---
description: Pull and run a SQL Server in Docker
---

# SQL Server

Pull Image

```text
docker pull mcr.microsoft.com/mssql/server:2017-latest
```

Run Image

```
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=A123456!" -p 1433:1433 --name sql-dev -d mcr.microsoft.com/mssql/server:2017-latest
```

{% hint style="info" %}
Run Powershell as elevated
{% endhint %}

Change sa password

```text
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "A123456!" -Q "ALTER LOGIN SA WITH PASSWORD='B123456!'"
```

Run sqlcmd in container

```
docker exec -it sql1 "bash"
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'A123456!'
```

Connect to SQL Server from outside

{% hint style="info" %}
Use the host ip with the port, for example 192.168.10.206,1433 and the sa login
{% endhint %}

