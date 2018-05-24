# docker-powerdns-postgresql
Postgresql image with PowerDNS schema integrated

This container creates the default schema provided by PowerDNS for the PostgreSQL backend.

Additionally a user is created with full rights to the tables and sequences:

**Database:** pdns<br>
**User:** pdns<br>
**Password:** V3ryS3cr3tP4$$w0rd<br>

The arguments to use are the same as for the [official postgres docker image](https://hub.docker.com/_/postgres/).

If you wish to change the username and/or password, simply edit the powerdns.sql file with the desired credentials.

This container works along with the [cajetan19/powerdns-pgsql](https://hub.docker.com/r/cajetan19/powerdns-pgsql/) container.

## Sample `docker run`
```
docker run --detach\
-p 5432:5432 \
--name pdns-pgsql \
--env POSTGRES_PASSWORD=P@$$w0rd \
--env POSTGRES_USER=admin \
--env PGDATA=/var/lib/postgresql/data/pgdata \
--volume /share/pdns/var/lib/postgresql/data/pgdata:/var/lib/postgresql/data/pgdata \
--volume /share/pdns/etc/postgresql:/etc/postgresql \
cajetan19/powerdns-postgresql
```
