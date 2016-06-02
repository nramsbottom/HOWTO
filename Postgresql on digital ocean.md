
# Create PostgreSQL Server on Dreamhost

Run the following commands with elevation

	apt-get update
	apt-get install -y postgresql

# Change PostgreSQL user password

This will allow you to manage the server without needing a password. Run the following command with elevation and specify the user password.

	passwd postgres

# Change PostgreSQL admin password

Switch to the PostgreSQL user.
	
	su - postgres
	psql

Run the following within the psql tool.

	\password postgres

Quit the tool with

	\q


# Show databases

Login as postgres user
	
	su - postgres
	psql

	# inside psql
	\l

# Create a database

	su - postgres
	psql

	# inside psql
	CREATE DATABASE testdb;

# Create database user

	su - postgres
	psql
	
	# inside psql
	CREATE USER testdbuser;

	GRANT ALL PRIVILEGES ON DATABASE testdb TO testdbuser;

# Login as user

	# note that -h localhost forces TCP socket
	psql -h localhost -U testdbuser -W

# Credits

This is based on:

- [http://www.techrepublic.com/blog/diy-it-guy/diy-a-postgresql-database-server-setup-anyone-can-handle/](http://www.techrepublic.com/blog/diy-it-guy/diy-a-postgresql-database-server-setup-anyone-can-handle/)
- [http://stackoverflow.com/questions/2942485/psql-fatal-ident-authentication-failed-for-user-postgres](http://stackoverflow.com/questions/2942485/psql-fatal-ident-authentication-failed-for-user-postgres)