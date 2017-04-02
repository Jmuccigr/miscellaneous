---
title: Working with php
author: John D. Muccigrosso
...

## Locally

### Using MAMP

1.  Use phpMyAdmin to manage databases.
    1.  Create database "temples".
    1.  Import temples csv into new table.
    1.  Select table and under "Operations", rename table.

### Uploading to hosting service

1. Export the local database to a .sql file using the `mysqldump` command. More details [here](http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/#more-184), but basically (note lack of space before password):

        mysqldump -u <username> -p<password> <database> > filename.sql
    
1. Zip the exported file.
1. With the mysql database wizard, select or create a new database that will be the target for the exported database. This assumes that the structure of the local database has not changed. If it has, modify the server version to match, or delete the relevant table.
1. In phpadmin select the target database and choose the import tab, selecting the .zip file. More details on this step [here](http://www.inmotionhosting.com/support/website/phpmyadmin/import-database-using-phpmyadmin).
