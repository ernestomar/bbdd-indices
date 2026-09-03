# Preparación del entorno

## MySQL con Docker

```sh
docker pull mysql:5-oracle

docker run --name mysql-indices -e MYSQL_ROOT_PASSWORD=12345678 -d mysql:5-oracle
```

## Instalar BBDD de ejemplo


1. Descargar la bbdd que esta en el archivo: employees_db.zip

2. Copie esta BBDD al contenedor 

```sh
docker cp employees_db.zip mysql-indices:/
```

4. Ingresar al contenedor

```sh
docker exec -it mysql-indices bash
````

5. Actualizar, instalar el unzip y cargar base de datos.

```sh
cd /
yum update
yum install unzip
unzip employees_db.zip
cd employees_db
mysql -u root -p < employees.sql
````

6. Ingresar al mysql.

mysql -u root -p

7. Revisar que exista la BBDD employees

SHOW DATABASES;
