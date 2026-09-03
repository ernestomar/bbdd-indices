# Preparación del entorno

## Extraemos los datos de prueba

```sh
unzip employees_db.zip
# Generar la carpeta employees_db
```

## MySQL con Docker

```sh
docker pull mysql:5-oracle

docker run --name mysql-indices -v ./employees_db:/employees_db -e MYSQL_ROOT_PASSWORD=12345678 -d mysql:5-oracle
```

## Instalar BBDD de ejemplo


1. Ingresar al contenedor

```sh
docker exec -it mysql-indices bash
````

5. Actualizar, instalar el unzip y cargar base de datos.

```sh
cd /employees_db
mysql -u root -p < employees.sql
````

6. Ingresar al mysql.

mysql -u root -p

7. Revisar que exista la BBDD employees

SHOW DATABASES;
