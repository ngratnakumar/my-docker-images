FROM centos/postgresql-94-centos7

# User name for PostgreSQL account to be created
ENV POSTGRESQL_USER				=	postgres

# Password for the user account
ENV POSTGRESQL_PASSWORD 		=	postgre$.2010

# Database name
ENV POSTGRESQL_DATABASE 		=	napsgoadb

# Password for the postgres admin account (optional)
# ENV POSTGRESQL_ADMIN_PASSWORD 	=	postgre$.2010

# # The following environment variables influence the PostgreSQL configuration file. They are all optional.

# The maximum number of client connections allowed. This also sets the maximum number of prepared transactions. (Default = 100)
ENV POSTGRESQL_MAX_CONNECTIONS 	=	100

# Sets how much memory is dedicated to PostgreSQL to use for caching data (Default = 32M)
ENV POSTGRESQL_SHARED_BUFFERS 	= 	32M

# Forwarding Postgresql port 5432 to host 5432
EXPOSE 5432 8080 8181 3000 80 443 22 

ENV PGDATA=/napsdata/naps-pgsql/pgsql/

# RUN initdb -d PGDATA=/var/lib/pgsql/
CMD initdb

# RUN pg_ctl -D PGDATA=/var/lib/pgsql -l logfile start

CMD pg_ctl -l logfile start

CMD /bin/bash 