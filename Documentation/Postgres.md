# Postgres SQL
These instructions will walk you through installing Postgres on Fedora.  
```
sudo dnf update
sudo dnf install postgresql-server postgresql-contrib
sudo postgresql-setup --initdb
sudo systemctl enable postgresql
sudo systemctl start postgresql
```
Let's verify Postgres is running.
```
sudo systemctl status postgresql
```
Postgres runs under a special user called **postgres**, switch to that user before entering the Postgres shell:
```
sudo -u postgres psql
```
Now, lets create a user and a database.
```
CREATE ROLE yourusername WITH LOGIN PASSWORD 'yourpassword';
ALTER ROLE yourusername CREATEDB;
CREATE DATABASE yourdatabase;
GRANT ALL PRIVILEGES ON DATABASE yourdatabase TO yourusername;
\q
```
Next, we will edit the configuration file to allow password authentication for local connections by editing the pg_hba.conf file.
```
sudo nano /var/lib/pgsql/data/pg_hba.conf
```
Find the line that looks like this:
```
local        all         all            peer
```
And change it to this:
```
local        all         all            md5
```
Save the file and exit.  
To apply the changes you will restart Postgres to apply the changes.
```
sudo systemctl restart postgresql
```
## Install PostgresSQL Node.js Client - pg
```
npm install pg
```
Once the pg library is installed, you can set up a connection to the PostgreSQL database:
```
const { Client } = require('pg');

const client = new Client({
  user: 'yourusername',
  host: 'localhost',
  database: 'yourdatabase',
  password: 'yourpassword',
  port: 5432,
});

client.connect()
  .then(() => {
    console.log("Connected to PostgreSQL database!");
  })
  .catch(err => {
    console.error("Connection error", err.stack);
  });

// Don't forget to close the connection when done
client.end();
```
```
node testscript.js
```
## Install pgAdmin (GUI Tool)
```
sudo dnf install pgadmin4
```
## See Also
* [Prisma](Prisma.md)