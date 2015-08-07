The following is my bash file for backup MySQL database.

## Usage of the bash file
1. Specify the database username and password
2. Add code to backup database, change the line backup blog to the database name need backup

`backup_blog.sh`

    #!/bin/bash
    
    db_user=username
    db_pwd=password
    backup() {
    	if [ -z "$1" ]
      	then
        	echo "-Parameter database is empty, please input the db name to backup"
      	else
      		echo "Backup database $1"
        	mysqldump -u$db_user -p$db_pwd $1 > $1.sql
      	fi
    }
    
    now=`date +"%Y%m%d%H%M%S"`
    echo Create directory $now
    mkdir ~/$now
    cd ~/$now
    
    # dump all except for table t_log
    # tables=$(mysql -u$db_user -p$db_pwd -N <<< "show tables from db_name" | grep -Ev "^t_log$" | xargs);
    # mysqldump -u$db_user -p$db_pwd db_name $tables > db_name.sql
    
    # dump structure for table t_log
    # mysqldump -u$db_user -p$db_pwd -d db_name t_log >> db_name.sql
    
    # blog database
    backup blog
    
    echo "Create tar file from backup folder"
    cd ~
    tar czf $now.tar.gz $now
    
    echo "Remove backup folder"
    rm -rf $now