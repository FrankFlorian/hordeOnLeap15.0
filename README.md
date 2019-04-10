


```
docker-compose -f docker-compose.yml up
docker exec -it hordeonleap150_db_1 mysql -p -e "create database horde; grant all on horde.* to 'horde'@'%' identified by 'horde'";
```
-> Password: horde

Use the frontend for building the new configuration: Go to the gear symbol select Administration->Configuration and then select the configuration for Horde(Horde (horde) 6.0.0-git).

Stay at Gernal tab and go to Session Settings:
```
$conf[cookie][domain] = ""
```
Go to database tag and fill in the following valus:
```
$conf['sql']['phptype'] = MySQL/PDO
$conf['sql']['username'] = horde
$conf['sql']['password'] = horde 
$conf['sql']['protocol'] = TCP/IP
$conf['sql']['hostspec'] = hordeonleap150_db_1
$conf['sql']['port'] = 3306
$conf['sql']['database'] = horde
$conf['sql']['charset'] = utf-8
$conf['sql']['ssl'] = No
$conf['sql']['splitread'] = Disabled
$conf['sql']['logqueries'] = no checkmark
```
docker exec -it hordeOnTumbelweed_php_1 /srv/git/horde/base/bin/horde-db-migrate
