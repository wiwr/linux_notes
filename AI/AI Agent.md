# Postgres db
	Database to store information
## Ubuntu / Debian

### 1. Update package lists

```
sudo apt update
```

### 2. Install PostgreSQL

```
sudo apt install postgresql postgresql-contrib -y
```

### 3. Start and enable the service

```
sudo systemctl enable postgresqlsudo systemctl start postgresql
```

### 4. Verify it's running

```
sudo systemctl status postgresql
```

You should see:

```
Active: active (running)
```

### 5. Switch to the PostgreSQL user

```
sudo -i -u postgres
```

### 6. Open the PostgreSQL shell

```
psql
```

### 7. Create a database

```
CREATE DATABASE myapp;
```

### 8. Create a user

```
CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypassword';
```

### 9. Grant privileges

```
GRANT ALL PRIVILEGES ON DATABASE myapp TO myuser;
```

### 10. Exit

```
\q
```

Exit the `postgres` user:

```
exit
```

## Verify the installation

Check the version:

```
psql --version
```

Example:

```
psql (PostgreSQL) 17.x
```

List databases:

```
sudo -u postgres psql -c "\l"
```
# Python
	Code that will do things 
1) include log utility
2) AI Agent class
3) 
