# Frappe db access denied issue

## Go to the mariadb container terminal

## Login to the mariadb with root credentials
```
mariadb -u root -p
```

## See the current user and host
```
SELECT user,host FROM mysql.user;
```

## Create user with any host
```
CREATE USER '<DB_NAME>'@'%' IDENTIFIED BY '<DB_PASSWORD>';
```

## Grant all permissions
```
GRANT ALL PRIVILEGES ON `<DB_NAME>`.*  TO '<DB_NAME>'@'%';
FLUSH PRIVILEGES;
```
