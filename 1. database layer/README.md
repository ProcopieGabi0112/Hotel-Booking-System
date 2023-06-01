# Oracle Database

## Technology stack  
- **Deployment**: Oracle Database v21.3 - Enterprise Edition (release April 30, 2024)

## Setting up 

1. Download zip file. 
   Download archive from https://www.oracle.com/ro/database/technologies/oracle-database-software-downloads.html .

2. Create in the path of `C:` folders `C:\oracle21c` and `C:\oracle21c\db`. 
   In the folder `C:\oracle21c\db` put the the archive and the unzipped file.

3. Seach for the file setup.exe in the path `C:\oracle21c\db`. Press right-clck on setup.exe file and access the file using the option of RUN AS ADMINISTRATOR

4. Intermediate steps

  ⚠️ Create and configure a single instance database 
  
  ⚠️ Desktop class
  
  ⚠️ Use Windows Build-in Account
  
5. Environment Setup

Base file of the database
```
 Oracle base:  `C:\oracle21c`
```

Database files location
```
 Database file location: `C:\oracle21c\db\oradata`
```
Name of database
```
 Global databse name: `orcl`
```
Password
```
 Password: `Gabi#230*********`
```

Pluggable database
```
 Pluggable database name: `orclpdb`
```

Check this alse
```
 Character set: `Unicode`
 ```
 
6. Save the Response.file in case u forgot the main database info

in order to ensure the installation is right check https://localhost:5500/em

## Connection to database as sys

Connect to [_system_] / [database-administrator] the create ur main users and schemas: 
```
Oracle SQL Developer environment:
  
 🔼 Name: admin 
 🔼 Username: sys/system
 🔼 Password: Gabi#230*********
 🔼 Hostname: localhost
 🔼 Port: 1521
 ⚠️ SID: orcl
   
```

Creating a user other than system user
```
--we will check if database is open
SELECT name, open_mode FROM v$pdbs;
--we will open pluggable database
ALTER PLUGGABLE DATABASE orclpdb OPEN;
--we will set session to orclpdb
ALTER SESSION SET CONTAINER=orclpdb;
--we will check if the user is already created
DROP USER app_db_admin;
--we will create user
CREATE USER app_db_admin IDENTIFIED BY pass;

--we will grant him permissions
GRANT CONNECT, RESOURCE TO app_db_admin;
GRANT CREATE SESSION TO app_db_admin;
GRANT CREATE TABLE TO app_db_admin;
GRANT CREATE VIEW TO app_db_admin;
GRANT CREATE PROCEDURE TO app_db_admin;
GRANT CREATE SEQUENCE TO app_db_admin;
GRANT CREATE TRIGGER TO app_db_admin;
GRANT CREATE TYPE TO app_db_admin; 
GRANT ALTER SESSION TO app_db_admin;
GRANT EXECUTE ANY PROCEDURE TO app_db_admin;

--we will close pluggable database
ALTER PLUGGABLE DATABASE orclpdb CLOSE;

--we will finish our job
COMMIT;

```

## Connection to database as app_db_admin

Connect to [_app_db_admin_] / [created user] the create ur main users and schemas: 
```
Oracle SQL Developer environment:
  
 🔼 Name: app_db_admin
 🔼 Username: app_db_admin
 🔼 Password: pass
 🔼 Hostname: localhost
 🔼 Port: 1521
 ⚠️ Service name: orclpdb
   
```
