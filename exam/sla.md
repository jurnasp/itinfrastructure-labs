Coverage:
 - Webserver configuration files
 - Ansible repository
 - DNS configuration files for master
 - Database servers database dumps

RPO:
7 days

Frequency:
A full backup will be performed every monday
A incremental backup will be performed on every day of the week

Retention:
28 days

Verification that eveything is working as intended after performing the restoration:
 - Database is operational and has its data back
 - The DNS service is up and running
 - The web server is operational

Restoration Criterie:
The backup files are usable and can be used to recover the correct state of the services

Storage:
Stored in two places: Firstly the webserver(/var/backup/files) and secondly the backup server(/srv/backup) and also on the ansible host machine. The configurations can also be found in the ansible files, using ansible will restore the services but it will not restore the database.
