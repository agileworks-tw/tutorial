# internal docker communicate

``` yml
version: '2'
services:
  dev:
    container_name: sailsSample_dev
    image: agileworks/sails_sample_env
    command: "/bin/sh -l -c 'npm i && npm start'"
    environment:
      PORT: "1337"
      NODE_ENV: "development"
      DOMAIN_HOST: "localhost:1337"

    ports:
      - "8000:1337"

    working_dir: /sailsSample
    volumes:
      - ./:/sailsSample
    depends_on:
      - "mysql"

  mysql:
    container_name: mysql
    image: dgraziotin/mysql
    expose:
      - "3306"
    environment:
      MYSQL_ADMIN_PASS: "root"
      MYSQL_USER_NAME: "nodejsSample"
      MYSQL_USER_DB: "nodejsSample"
      MYSQL_USER_PASS: "nodejsSample"
      CREATE_MYSQL_BASIC_USER_AND_DB: "true"

    volumes:
      - mysql-data:/var/lib/mysql/

  backup:
    image: ubuntu
    volumes:
      - ./:/backup
      - mysql-data:/dbdata
    command: "tar cvf /backup/backup.tar /dbdata"

  restore:
    image: ubuntu
    volumes:
      - ./:/backup
      - mysql-data:/dbdata
    working_dir: /dbdata
    command: "tar xvf /backup/backup.tar --strip 1"


volumes:
  mysql-data:
    driver: local

```
