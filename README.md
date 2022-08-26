# Gitea Docker Compose

You can access the project through the following link: https://repositories.homelab.

## Config Files:

We added a help file with the default configuration to connect Gitea and the OpenLDAP. Check the [ldap.txt](help/ldap.txt "ldap file") file.

If you want, you can create a [app.ini](config/app.ini "app.ini") file and set some default configurations.

## Folders:

1. Default folder.

``` bash
  /data/gitea
```

2. app.ini folder.

``` bash
  /data/gitea/conf
```

3. Log folder.

``` bash
  /data/gitea/log
````

4. Folder to add the certificates.

``` bash
  /etc/ssl/certs/
```

## Commands:

1. Enter the container.

``` bash
  docker exec -it gitea bash
```

## Backup:

``` bash
  su git
  cd /app/backup/ && /app/gitea/gitea dump -c /data/gitea/conf/app.ini
```

## Restore:

``` bash
  unzip gitea-dump-*.zip
  mv custom/conf/app.ini /data/gitea/conf/app.ini

  unzip gitea-repo.zip
  mv repositories/* /data/git/repositories/

  chown -R gitea:gitea /data/gitea/conf/app.ini /data/git/repositories/

  mssql -u$USER -p$PASS $DATABASE < gitea-db.sql
  service gitea restart
```

## References:

1. [Installation with Docker.](https://docs.gitea.io/pt-br/install-with-docker "Installation with Docker")

1. [Database error on startup after upgrade to 1.5.0.](https://wiki.archlinux.org/index.php/Gitea "Database error on startup after upgrade to 1.5.0")

1. [Gitea Configuration LDAP.](http://www.jouvinio.net/wiki/index.php/Gitea_Configuration_LDAP "Gitea Configuration LDAP")

1. [Backup and Restore.](https://docs.gitea.io/pt-br/backup-and-restore "Backup and Restore")

## License:

[MIT](LICENSE "MIT License")

## Created by: 

1. Luciano Sampaio.
