# ccf_fdw
Foreign Data Wrapper (FDW) sample

# Build
sudo make install


# Install postgres
```
sudo apt-get install postgresql-12 postgresql-server-dev-12 -y
sudo pg_ctlcluster 12 main start
sudo /etc/init.d/postgresql reload
sudo service postgresql restart
```

# Connect to postgres
```
sudo su - postgres
psql
```

# setup wrapper
CREATE EXTENSION hello_fdw;
CREATE SERVER hello
  FOREIGN DATA WRAPPER hello_fdw
  OPTIONS (host 'postgres.example.com', dbname 'my_app');
CREATE FOREIGN TABLE films (
    code        varchar NOT NULL,
    title       varchar(40) NOT NULL
)
SERVER hello;
SELECT * FROM  films;

\detr