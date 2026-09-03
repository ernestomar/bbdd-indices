## Indices

1. Si no hay llave primaria no se crea ningún indice.

```sql
-- Creo una tabla sin llave primaria

CREATE TABLE registro_visitas (
    nombre      VARCHAR(100) NOT NULL,
    fecha       DATE NOT NULL,
    comentario  TEXT
);

SHOW INDEX FROM registro_visitas;
```

2.  Si la tabla tiene llave primaria, esa llave oficia como indice. Además al definir una columna como UNIQUE

```sql
CREATE TABLE clientes (
    id            INT AUTO_INCREMENT,
    nombre        VARCHAR(100) NOT NULL,
    email         VARCHAR(150) NOT NULL UNIQUE,
    fecha_alta    DATE,
    PRIMARY KEY (id)
);

SHOW INDEX FROM clientes;
```

3. Las llaves foraneas tambien generan indices en MySQL (En Postgresql no).

```sql
CREATE TABLE pedidos (
    id           INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id   INT NOT NULL,
    fecha        DATETIME DEFAULT CURRENT_TIMESTAMP,
    total        DECIMAL(10,2) NOT NULL,
    CONSTRAINT fk_pedidos_cliente
        FOREIGN KEY (cliente_id) REFERENCES clientes(id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
) ENGINE=InnoDB;

SHOW INDEX FROM pedidos;
```