# Expense Tracker

A simple command line based expense tracker.


## Requirements
1. Ruby 2.6 onwards (Provided for in Cloud 9 Amazon Linux 2 Platform)
2. PostgreSQL
3. `pg` gem to interact with the PostgreSQL database. 
4. Bundler gem (Provided for in Cloud 9 Amazon Linux 2 Platform)

## Setup
Install PostgreSQL and `pg` gem on Cloud 9, follow the following steps:
1. Choose Amazon Linux 2 Platform
2. Enter the following commands in cloud9 terminal
  ```terminal
  sudo yum install postgresql postgresql-server postgresql-libs  postgresql-devel
  
  sudo amazon-linux-extras install postgresql14
  
  gem install pg
  ```

3. Initialize and start the database. 
  ```terminal
  sudo service postgresql initdb
  sudo service postgresql start
  ```
  **Note:** We just need to initialize once but we have to start the database
  everytime we reconnect to cloud 9.
  
4. Create role and database for "ec2-user" (the default username for cloud9 user)
in PostgreSQL. See [here](https://launchschool.com/books/sql/read/preparations#installingpostgresql)
for more information
  ```terminal
  sudo -u postgres createuser -s ec2-user
  sudo -u postgres createdb ec2-user
  ```
It will complain of  `could not change directory to "/home/ec2-user/environment": Permission denied` but the role and database will still be created.

5. Create the database
  ```terminal
  createdb expenses
  psql -d expenses < schema.sql
  ```

## Usage
### List all commands
```terminal
./expenses
```

### Add an expense
```terminal
./expenses add 4.50 "Coffee"
./expenses add 125 "Petrol"
./expenses add 1299.00 "Macbook Air"
```

### List all expenses
```terminal
./expenses list
```

### Delete an expense by its index
```terminal
./expenses delete 0
```

### Search for an expense
```terminal
./expenses search "Macbook"
```

### Delete all expenses
```terminal
./expenses clear
```