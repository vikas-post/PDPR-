# PDPR-
Postgres Database and Performance Report 
This report is equivalent to the AWR report in Oracle. It also work as the same way AWR report works in Oracle. 
The report works for single datbase. So if you have multiple database then you have to setup multiple report.
The report will run using postgres user or the default user. 
There are multiple script which is used to generate the report and there are multiple extension which we are using in the script. 
Before start please make sure that you have below extesion in your postgres database 
1. File-FDW 
2. pg_stat_statements 

Now the first step is to create the schema which will store the data. To create the schema we will use the below script 

schema_creation.sh 

run this script in the shell with database name ie schema_creation.sh <dbname>

This shell script call another script which is SQL file schema_creation.sql. 

These script will create PDPR schema in your database. 

Once schema will create take a restart of the database because we are doing some changes in postgresql.conf file which need restart of the database.

After that setup the cronjob to collect the data according to the time intervel you need. 

script used for snapshot : snapshot_creation.sh <dbname> <hostname>
it will call another script which is snapshot_creation.sql

To generate the report run the scipt gen_report.sh <dbname> and it will ask you number of questions and it will generate the report for you in HTML format. 
