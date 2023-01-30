#  Keycloak Migration 13 Version To 19 Version With Postgres SQL  And mssql Databases

## Postgres SQL Database :-

## 1. What is PostgreSQL?

PostgreSQL (often shortened to simply "Postgres") is an advanced Relational DataBase Management System ("RDBMS"), that lets you efficiently and securely store any type of data. 

## How to Deploye  PostgreSQL ?

- I have created a 3 yaml files . their StatefulSet.yaml, service.yaml and storageclass.yaml files . 

- In deployment files thier added a postgres images   ,  POSTGRES_USERS, POSTGRES_PASSWORD, POSTGRES_DB and Container ports.

- In service files i have created a kind name and postgrtes ports.

### POSTGRES SQL DATABASE :-

-    I have created a Database in postgres named as keycloak .
-  and database schema named as public

  -       sudo kubectl -n namespace exec -it podname -- bash
  -       su -postgres
  -       psql --host localhost --username postgres
  -       psql
  -       psql -h localhost -U postgres -P
  -       \C (connect the database)  
  -       create database databasename;
  -       \c databasename;
  -       \l (list of database)
  -       create schema name;
  -       \dt (show tables)

### Screenshots

![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r5315780688184977&th=186014452e53c1c4&view=att&disp=safe&realattid=f_ldiekn0p0)

### 2. How to integrated Keycloak 13.0.1 version with postgres Database ?
- I have created a deployment.yaml file,pv.yaml,pvc.yaml,service.yaml and ingress.yaml files.
- In deployment file , i have added pvc name,keycloak images, KEYCLOAK_USER      ,               KEYCLOAK_PASSWORD    , DB_VENDOR , DB_ADDR  , DB_PORT   ,DB_DATABASE    ,DB_USER    ,          DB_PASSWORD.



### Screenshots

![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r2900390430172675482&th=1860158497a00de4&view=att&disp=safe&realattid=f_ldifcws30)

- some of the following commands :
   
   -     \c realm
   -     select * from realm;
   -     \c redirct_uris
   -     select * from public.user_entity;

### Screenshots
![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r5439458034287930978&th=18601a03f195218a&view=att&disp=safe&realattid=f_ldii5yzy0)

![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r6820302638020333740&th=18601a1830ce040f&view=att&disp=safe&realattid=f_ldii7r1l0)


### 2. How to integrated Keycloak 19.0.1 version with postgres Database ?

It is similar as keycloak 13.0.1 version , only i have to change the images.

### Screenshots
![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r-2795047653662701863&th=186018d031e7913d&view=att&disp=safe&realattid=f_ldihez6d0)


## MSSQL Database :-


###  1. What is Mssql?

MSSQL is a suite of database software published by Microsoft and used extensively within our enterprise. Typically, it includes a relational database engine, which stores data in tables, columns and rows, Integration Services (SSIS).

### How to Deploye MSSQL ?

-  I have created a 3 yaml files , ie  deployment.yaml   , pvc.yaml  and  service.yaml .

-   In deployment I have added images   , MSSQL_USER , ACCEPT_EULA  , SA_PASSWORD and MSSQL_DB.

- some of the following commands :

-      kubectl -n namespace exec -it podname -- bash
-      /opt/mssql-tools/bin/sqlcmd -S [cluster ip] -U [username] -P [password]
-     1> CREATE DATABASE DATABASENAME [KEYCLOAK]
      2> GO
-     1> USE DATABASENAME [KEYCLOAK]
      2> GO


### Screenshots
![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r-5917500372379459514&th=18601b6d58db54b1&view=att&disp=safe&realattid=f_ldij1q8d0)


### 1. How to integrated Keycloak 13.0.1 version with MSSQL Database ?

- I have created a deployment.yaml file,pv.yaml,pvc.yaml,service.yaml and ingress.yaml files.
- In deployment file , i have added pvc name,keycloak images, KEYCLOAK_USER , KEYCLOAK_PASSWORD , DB_VENDOR , DB_ADDR , DB_PORT ,DB_DATABASE ,DB_USER , DB_PASSWORD.

### Screenshots
![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r4066809743292372567&th=186020caa26d31c0&view=att&disp=safe&realattid=f_ldime9b50)

- some of the following commands in mssql bash.

-     1> SELECT * FROM SYS.DATABASES;
      2> GO

-     1> USE DATABASENAME [KEYCLOAK]
      2> GO
-     1>SELECT * FROM INFORMATION_SCHEMA.TABLES;
      2> GO
-     1>SELECT * FROM REALM;
      2> GO
-     1>SELECT * FROM USER_ENTITY;
      2> GO

### Screenshots
![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.1&permmsgid=msg-a:r-7701035232932452695&th=1860210dfc15ff1d&view=att&disp=safe&realattid=f_ldimk6j20) 

![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.2&permmsgid=msg-a:r-7701035232932452695&th=1860210dfc15ff1d&view=att&disp=safe&realattid=f_ldimk6j71) 


### 2. How to integrated Keycloak 19.0.1 version with MSSQL Database ?

It is similar as keycloak 13.0.1 version , only i have to change the images.

![App Screenshot](https://mail.google.com/mail/u/0?ui=2&ik=3a18febced&attid=0.2&permmsgid=msg-a:r4066809743292372567&th=186020caa26d31c0&view=att&disp=safe&realattid=f_ldime9bb1)


### Note :

I have succesfully deployed postgressql database and mssql databases with keycloak 13.0.1 and 19.0.1 all data are stored in the following database.
