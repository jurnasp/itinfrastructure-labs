1) Recovery from the backup server:
 a) If the dns service is running:
  - duplicity --no-encryption restore rsync://infra02.sbo.ttu//srv/backup/ /var/backup/restore/
 b) If the dns service is down:
  - duplicity --no-encryption restore rsync://192.168.56.4//srv/backup/ /var/backup/restore/
2) Fully restore from the backups(Requires employee with access to backupAgent user):
 - sudo /var/backup/script/restoration_script
3) Verify that everything is working as intended:
 a) Webservice status:
  - systemctl status apache2
  - wget -qO- 192.168.56.4:80
  - wget -qo- 192.168.56.4:8080
 b) Database state:
  - Confirm that the tables and data is up to date by using mysql queries
 c) DNS service status:
  - dig ns.sbo.ttu
  - host 192.168.56.4
  - host 192.168.56.5
