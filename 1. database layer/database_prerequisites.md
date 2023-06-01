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

## Connection to database

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
CREATE USER app_user IDENTIFIED BY pass;

GRANT CREATE SESSION TO app_user;
GRANT CREATE TABLE TO app_user;
GRANT CREATE VIEW TO nume_utilizator;
GRANT CREATE PROCEDURE TO app_user;
GRANT CREATE SEQUENCE TO app_user;
GRANT CREATE TRIGGER TO app_user;
GRANT CREATE FUNCTION TO app_user;
GRANT CREATE TYPE TO app_user; 
GRANT CREATE INDEX TO app_user;
GRANT ALTER SESSION TO app_user;
GRANT EXECUTE ANY PROCEDURE TO app_user;

```
