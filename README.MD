# Firebird Dockerfile



## Description

Firebird 1.5.6 SuperServer

### Provides

  Firebird SQL relational database (http://www.firebirdsql.org/).

### Volumes

 * /backup
 * /data

### Exposed Ports

 * 3050

### Firebird credentials

 * Username: SYSDBA
 * Password: masterkey

## Run

	$ docker run -d \
		--name firebird \	
		-p 3050:3050 \
		-v /somehostdir/firebird/backup/:/backup/ \
		-v /somehostdir/firebird/data/:/data/ \
		mladenp87/firebird1.5.6-ss

## Misc

### Restore backup

	//enter container console
	$ docker exec -i -t firebird /bin/bash

    //backup
    $ gbak -v -t -user SYSDBA -password masterkey localhost:/data/dbname.fdb /backup/dbname.fbk 

     //restore 
	$ gbak -c -v -user SYSDBA -password masterkey /backup/dbname.fbk localhost:/data/dbname.fdb
