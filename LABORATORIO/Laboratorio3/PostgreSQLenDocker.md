# 🧑🏽‍💻Practica 04 - PostgreSQL en Docker para Ingeniería de Datos

## 1. Objetivo de la práctica

En esta práctica se ha trabajado con **PostgreSQL ejecutándose dentro de
un contenedor Docker** en un servidor Ubuntu.

El objetivo principal es simular un pequeño proceso de Ingeniería de
Datos en el que partimos de un archivo CSV con información de ventas, lo
introducimos en un contenedor PostgreSQL, almacenamos los datos en una
tabla de staging y posteriormente realizamos diferentes consultas para
comprobar y analizar la información.

El flujo general realizado ha sido:

**Archivo CSV → Docker → PostgreSQL → tabla staging → validación →
análisis de datos**

De esta forma, además de trabajar con PostgreSQL, se practican conceptos
básicos de Docker como imágenes, contenedores, puertos, logs, ejecución
de comandos dentro de contenedores, copia de archivos y gestión del
ciclo de vida de un contenedor.

------------------------------------------------------------------------

## 2. Entorno utilizado

La práctica se ha realizado desde **Windows**, utilizando la **Terminal de Windows** para conectarme al servidor **Ubuntu Server mediante SSH**.

Una vez establecida la conexión SSH, todas las operaciones de la práctica se realizan sobre el servidor Ubuntu, donde está instalado **Docker Engine**.

El entorno utilizado es:

**Windows**
↓
**Terminal de Windows**
↓
**Conexión SSH**
↓
**Ubuntu Server**
↓
**Docker Engine**
↓
**Contenedor PostgreSQL 16**

La conexión mediante SSH permite trabajar con el servidor Ubuntu desde la Terminal de Windows como si se estuviera trabajando directamente en él. A partir de ahí, se utilizan los comandos de Docker para descargar la imagen de PostgreSQL, crear el contenedor y realizar las diferentes operaciones de la práctica.


------------------------------------------------------------------------

## 3. Comprobación de Docker

### Teoría

Antes de comenzar es necesario comprobar que Docker está correctamente
instalado y funcionando en el servidor.

Para ello se utiliza `docker --version`, que permite consultar la
versión instalada de Docker.

También se pueden consultar los contenedores existentes mediante
`docker ps` y las imágenes disponibles mediante `docker images`.

### Práctica

Ejecuté el siguiente comando:

``` bash
docker --version
```

**Resultado:**

> 📸 **CAPTURA 1 --- Versión de Docker**

La salida permite comprobar que Docker está instalado correctamente en
el servidor.

A continuación comprobé los contenedores que estaban actualmente en
ejecución:

``` bash
docker ps
```

**Resultado:**

> 📸 **CAPTURA 2 --- `docker ps`**

Finalmente comprobé las imágenes disponibles:

``` bash
docker images
```

**Resultado:**

> 📸 **CAPTURA 3 --- `docker images`**

------------------------------------------------------------------------

## 4. Descarga de la imagen PostgreSQL

### Teoría

Docker utiliza **imágenes** como plantillas a partir de las cuales se
crean los contenedores.

En este caso se utiliza la imagen oficial de PostgreSQL en su versión
16.

Para descargarla se utiliza `docker pull`.

### Práctica

Ejecuté:

``` bash
docker pull postgres:16
```

**Resultado:**

> 📸 **CAPTURA 4 --- Descarga de `postgres:16`**

Una vez finalizada la descarga, comprobé que la imagen estaba
disponible:

``` bash
docker images
```

**Resultado:**

> 📸 **CAPTURA 5 --- Imagen PostgreSQL**

La presencia de `postgres` con la etiqueta `16` confirma que la imagen
se ha descargado correctamente.

------------------------------------------------------------------------

## 5. Creación del contenedor PostgreSQL

### Teoría

Una imagen Docker es una plantilla, mientras que un **contenedor** es
una instancia creada a partir de esa imagen.

Para crear el contenedor se utiliza `docker run`.

En esta práctica se configura PostgreSQL mediante diferentes parámetros:

-   `-d`: ejecuta el contenedor en segundo plano.
-   `--name postgres-data`: asigna el nombre `postgres-data`.
-   `-e POSTGRES_PASSWORD=curso123`: establece la contraseña del usuario
    administrador.
-   `-e POSTGRES_DB=empresa`: crea inicialmente la base de datos
    `empresa`.
-   `-p 5432:5432`: publica el puerto de PostgreSQL del contenedor en el
    puerto 5432 del servidor.

### Práctica

Ejecuté:

``` bash
docker run -d --name postgres-data -e POSTGRES_PASSWORD=curso123 -e POSTGRES_DB=empresa -p 5432:5432 postgres:16
```

**Resultado:**

> 📸 **CAPTURA 6 --- Creación del contenedor**

El contenedor queda creado con el nombre `postgres-data` y utilizando
PostgreSQL 16.

------------------------------------------------------------------------

## 6. Comprobación del contenedor

Para comprobar que PostgreSQL se está ejecutando correctamente utilicé:

``` bash
docker ps
```

**Resultado:**

> 📸 **CAPTURA 7 --- Contenedor PostgreSQL funcionando**

En la columna de puertos se puede observar la publicación:

``` text
5432->5432
```

Esto permite acceder al servicio PostgreSQL a través del puerto 5432 del
servidor.

------------------------------------------------------------------------

## 7. Comprobación de los logs

### Teoría

Los logs permiten consultar los mensajes generados por un contenedor.

En el caso de PostgreSQL son especialmente útiles para comprobar si el
servicio se ha iniciado correctamente y está preparado para aceptar
conexiones.

### Práctica

Ejecuté:

``` bash
docker logs postgres-data
```

**Resultado:**

> 📸 **CAPTURA 8 --- Logs de PostgreSQL**

Entre los mensajes de inicialización se puede comprobar que PostgreSQL
ha terminado de arrancar y está preparado para aceptar conexiones.

------------------------------------------------------------------------

## 8. Acceso a PostgreSQL

Para acceder directamente al servidor PostgreSQL desde el contenedor
utilicé `docker exec`:

``` bash
docker exec -it postgres-data psql -U postgres -d empresa
```

**Resultado:**

> 📸 **CAPTURA 9 --- Acceso a PostgreSQL / prompt `empresa=#`**

El prompt:

``` text
empresa=#
```

indica que la conexión se ha realizado correctamente y que ya es posible
ejecutar instrucciones SQL.

------------------------------------------------------------------------

## 9. Creación de la tabla de staging

### Teoría

Una tabla de **staging** sirve como zona intermedia para recibir datos
procedentes de una fuente externa antes de realizar procesos posteriores
de validación o transformación.

En este caso la fuente será un archivo CSV con información de ventas.

### Práctica

Dentro de PostgreSQL creé la tabla:

``` sql
CREATE TABLE staging_ventas (
    id INTEGER,
    fecha DATE,
    producto VARCHAR(100),
    cantidad INTEGER,
    precio NUMERIC(10,2)
);
```

**Resultado:**

> 📸 **CAPTURA 10 --- Creación de `staging_ventas`**

Posteriormente comprobé su contenido:

``` sql
SELECT * FROM staging_ventas;
```

**Resultado:**

> 📸 **CAPTURA 11 --- Tabla vacía**

La tabla aparece inicialmente vacía porque todavía no se han cargado los
datos del CSV.

Para salir de PostgreSQL:

``` text
\q
```

------------------------------------------------------------------------

## 10. Creación del archivo CSV

### Teoría

El archivo CSV representa una fuente de datos externa. En un entorno
real podría proceder de un sistema de ventas, una aplicación empresarial
o cualquier otro sistema que genere información estructurada.

Para esta práctica se utiliza un pequeño dataset de ejemplo.

### Práctica

Creé el archivo `ventas.csv` con los siguientes datos:

``` text
id,fecha,producto,cantidad,precio
1,2026-09-01,Portatil,2,1200.00
2,2026-09-01,Monitor,5,350.00
3,2026-09-02,Teclado,10,75.00
4,2026-09-02,Raton,15,35.00
5,2026-09-03,Portatil,1,1350.00
```

Para comprobar el contenido utilicé:

``` bash
cat ventas.csv
```

**Resultado:**

> 📸 **CAPTURA 12 --- Contenido de `ventas.csv`**

------------------------------------------------------------------------

## 11. Copia del CSV al contenedor

### Teoría

El comando `docker cp` permite copiar archivos entre el sistema
anfitrión y un contenedor Docker.

En este caso se utiliza para introducir el archivo CSV en el contenedor
PostgreSQL.

### Práctica

Ejecuté:

``` bash
docker cp ventas.csv postgres-data:/tmp/ventas.csv
```

Después comprobé que el archivo se encontraba dentro del contenedor:

``` bash
docker exec postgres-data ls /tmp
```

**Resultado:**

> 📸 **CAPTURA 13 --- `ventas.csv` dentro del contenedor**

También comprobé directamente su contenido:

``` bash
docker exec postgres-data cat /tmp/ventas.csv
```

**Resultado:**

> 📸 **CAPTURA 14 --- Contenido del CSV dentro del contenedor**

------------------------------------------------------------------------

## 12. Carga de los datos en PostgreSQL

Una vez que el CSV se encuentra dentro del contenedor, accedí nuevamente
a PostgreSQL:

``` bash
docker exec -it postgres-data psql -U postgres -d empresa
```

Posteriormente ejecuté:

``` sql
COPY staging_ventas
FROM '/tmp/ventas.csv'
DELIMITER ','
CSV HEADER;
```

**Resultado:**

> 📸 **CAPTURA 15 --- Resultado de `COPY`**

El mensaje:

``` text
COPY 5
```

indica que PostgreSQL ha cargado correctamente **5 registros** en la
tabla `staging_ventas`.

------------------------------------------------------------------------

## 13. Validación de los datos

### Teoría

En un proceso de Ingeniería de Datos no es suficiente con cargar la
información. Es necesario comprobar que los datos se han incorporado
correctamente.

Por este motivo se realizan diferentes consultas de validación.

### Comprobación de los registros

``` sql
SELECT * FROM staging_ventas;
```

**Resultado:**

> 📸 **CAPTURA 16 --- Registros cargados**

Se comprueba que los registros del CSV están presentes en la tabla.

### Número de registros

``` sql
SELECT COUNT(*)
FROM staging_ventas;
```

**Resultado:**

> 📸 **CAPTURA 17 --- `COUNT(*)`**

El resultado esperado para el dataset utilizado es:

``` text
5
```

Por tanto, el número de registros coincide con los cinco registros
existentes en el CSV de origen.

------------------------------------------------------------------------

## 14. Consulta analítica

Además de validar los datos, realicé una primera consulta de análisis:

``` sql
SELECT
    producto,
    SUM(cantidad * precio) AS importe_ventas
FROM staging_ventas
GROUP BY producto
ORDER BY importe_ventas DESC;
```

**Resultado:**

> 📸 **CAPTURA 18 --- Consulta de ventas por producto**

Esta consulta permite calcular el importe total de ventas agrupado por
producto.

El proceso realizado hasta este punto puede representarse de la
siguiente forma:

**CSV → Staging → Validación → Agregación → Información analítica**

------------------------------------------------------------------------

## 15. Inspección del contenedor

Una vez realizadas las operaciones sobre PostgreSQL, comprobé
información interna del contenedor mediante:

``` bash
docker inspect postgres-data
```

**Resultado:**

> 📸 **CAPTURA 19 --- `docker inspect`**

Este comando permite consultar diferentes parámetros de configuración
del contenedor, como su estado, imagen, nombre y configuración de red.

------------------------------------------------------------------------

## 16. Consulta del puerto

Para comprobar la publicación del puerto utilicé:

``` bash
docker port postgres-data
```

**Resultado:**

> 📸 **CAPTURA 20 --- `docker port`**

La salida permite comprobar que el puerto 5432 de PostgreSQL está
publicado en el servidor.

------------------------------------------------------------------------

## 17. Comprobación de recursos

Para observar los recursos utilizados por PostgreSQL ejecuté:

``` bash
docker stats postgres-data
```

**Resultado:**

> 📸 **CAPTURA 21 --- `docker stats`**

Se pueden observar diferentes métricas, entre ellas:

-   CPU utilizada.
-   Memoria utilizada.
-   Porcentaje de memoria.
-   Entrada y salida de red.

Para salir de `docker stats`:

``` text
Ctrl + C
```

------------------------------------------------------------------------

## 18. Detener y volver a iniciar el contenedor

### Teoría

Docker permite detener un contenedor sin eliminarlo.

Para detener PostgreSQL utilicé:

``` bash
docker stop postgres-data
```

Posteriormente comprobé los contenedores en ejecución:

``` bash
docker ps
```

**Resultado:**

> 📸 **CAPTURA 22 --- Contenedor detenido**

Aunque ya no aparece en `docker ps`, el contenedor continúa existiendo.
Esto se puede comprobar mediante:

``` bash
docker ps -a
```

**Resultado:**

> 📸 **CAPTURA 23 --- Contenedor con estado `Exited`**

A continuación volví a iniciar el mismo contenedor:

``` bash
docker start postgres-data
```

Y comprobé nuevamente su estado:

``` bash
docker ps
```

**Resultado:**

> 📸 **CAPTURA 24 --- Contenedor iniciado de nuevo**

------------------------------------------------------------------------

## 19. Comprobación de los datos después de reiniciar

Después de iniciar nuevamente el contenedor, accedí a PostgreSQL:

``` bash
docker exec -it postgres-data psql -U postgres -d empresa
```

Y ejecuté:

``` sql
SELECT * FROM staging_ventas;
```

**Resultado:**

> 📸 **CAPTURA 25 --- Datos después de `docker start`**

Los registros continúan disponibles porque se ha detenido y vuelto a
iniciar **el mismo contenedor**.

Esto permite diferenciar entre:

``` text
docker stop
      ↓
El contenedor permanece
      ↓
docker start
      ↓
Se vuelve a utilizar el mismo contenedor
```

------------------------------------------------------------------------

## 20. Reinicio del contenedor

También comprobé el comando `docker restart`:

``` bash
docker restart postgres-data
```

Después verifiqué nuevamente que PostgreSQL estaba activo:

``` bash
docker ps
```

**Resultado:**

> 📸 **CAPTURA 26 --- `docker restart`**

------------------------------------------------------------------------

## 21. Eliminación del contenedor

Finalmente comprobé la diferencia entre detener un contenedor y
eliminarlo.

Primero lo detuve:

``` bash
docker stop postgres-data
```

Después lo eliminé:

``` bash
docker rm postgres-data
```

Y comprobé los contenedores existentes:

``` bash
docker ps -a
```

**Resultado:**

> 📸 **CAPTURA 27 --- Contenedor eliminado**

Al eliminar el contenedor, ya no aparece `postgres-data`.

Este paso permite comprender la importancia de utilizar **Docker
Volumes** cuando necesitamos conservar los datos aunque eliminemos el
contenedor.

------------------------------------------------------------------------

## 22. Diferencia entre imagen y contenedor

Aunque el contenedor se haya eliminado, la imagen de PostgreSQL puede
continuar disponible.

Para comprobarlo:

``` bash
docker images
```

**Resultado:**

> 📸 **CAPTURA 28 --- Imagen `postgres:16`**

Esto demuestra que:

**Imagen ≠ Contenedor**

La imagen funciona como una plantilla, mientras que el contenedor es una
instancia creada a partir de dicha imagen.

------------------------------------------------------------------------

## 23. Eliminación de la imagen

Como último paso de limpieza, eliminé la imagen:

``` bash
docker rmi postgres:16
```

Finalmente comprobé las imágenes disponibles:

``` bash
docker images
```

**Resultado:**

> 📸 **CAPTURA 29 --- Imagen eliminada**

------------------------------------------------------------------------

## 24. Comandos Docker utilizados

  Comando              Función
  -------------------- -------------------------------------------
  `docker --version`   Comprobar la versión de Docker
  `docker pull`        Descargar una imagen
  `docker images`      Consultar las imágenes disponibles
  `docker run`         Crear y ejecutar un contenedor
  `docker ps`          Consultar contenedores activos
  `docker ps -a`       Consultar todos los contenedores
  `docker logs`        Consultar los logs
  `docker exec`        Ejecutar comandos dentro de un contenedor
  `docker cp`          Copiar archivos hacia/desde un contenedor
  `docker inspect`     Consultar información del contenedor
  `docker port`        Consultar los puertos publicados
  `docker stats`       Consultar el consumo de recursos
  `docker stop`        Detener un contenedor
  `docker start`       Iniciar un contenedor detenido
  `docker restart`     Reiniciar un contenedor
  `docker rm`          Eliminar un contenedor
  `docker rmi`         Eliminar una imagen

------------------------------------------------------------------------

## 25. Flujo completo del laboratorio

``` text
ventas.csv
    │
    │ docker cp
    ▼
┌──────────────────────────┐
│ Docker Container         │
│                          │
│ PostgreSQL               │
│ ┌──────────────────────┐ │
│ │ staging_ventas       │ │
│ │                      │ │
│ │ id                   │ │
│ │ fecha                │ │
│ │ producto             │ │
│ │ cantidad             │ │
│ │ precio               │ │
│ └──────────────────────┘ │
└──────────────────────────┘
             │
             │ SQL
             ▼
       Validación
             │
             ▼
       Transformación
             │
             ▼
       Datos analíticos
```

------------------------------------------------------------------------

## 26. Conclusión

En esta práctica se ha realizado un flujo completo de trabajo con
**Docker y PostgreSQL**, comenzando con la descarga de la imagen y
terminando con la eliminación de los recursos utilizados.

Durante el proceso se ha trabajado con la creación y gestión de
contenedores, la publicación de puertos, la consulta de logs, la
ejecución de comandos mediante `docker exec` y la transferencia de
archivos mediante `docker cp`.

Desde el punto de vista de Ingeniería de Datos, se ha realizado un
pequeño proceso de tratamiento de datos partiendo de un archivo CSV como
fuente de datos, introduciéndolo en una tabla de staging de PostgreSQL y
realizando posteriormente consultas para validar y analizar la
información.

También se ha comprobado la diferencia entre **imagen y contenedor**,
así como la diferencia entre detener un contenedor y eliminarlo.

Finalmente, la práctica sirve como introducción al concepto de **Docker
Volumes**, que permite conservar los datos independientemente del ciclo
de vida del contenedor.

---
