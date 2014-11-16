# mysql
### optimize all databases
    mysqlcheck -u root -p --optimize --all-databases

### backup / mysqldump
single database:

    mysqldump -uroot databasename|bzip2 > ~/backups/databasename-$(date +%Y-%m-%d).sql.bz2

all databases:

    for i in $(mysql -e 'show databases' -uroot -s --skip-column-names|grep -v information_schema|grep -v performance_schema);do mysqldump -uroot $i|xz -z -9 -c > ~/backups/$i-$(date +%Y-%m-%d).sql.xz;done

### mysql restore
    mysql -u root dbname < database.sql

### dump and restore live via ssh
    mysqldump --all-databases | ssh user@host mysql

### create new user
    CREATE USER 'dbname'@'localhost' IDENTIFIED BY  'password';
    GRANT USAGE ON * . * TO  'dbname'@'localhost' IDENTIFIED BY  'password' WITH MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;
    CREATE DATABASE IF NOT EXISTS  `dbname`;
    GRANT ALL PRIVILEGES ON  `dbname` . * TO  'dbname'@'localhost';

### drop user
    DROP USER user@host;
    DROP DATABASE name;

