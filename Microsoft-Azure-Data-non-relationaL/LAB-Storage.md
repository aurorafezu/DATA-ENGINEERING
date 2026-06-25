# Práctica de Laboratorio: Exploración de Azure Storage


# 1. Introducción

En esta práctica se exploran los principales servicios de almacenamiento no relacional ofrecidos por Microsoft Azure mediante la creación y configuración de una cuenta de almacenamiento.

Los servicios analizados son:

- **Azure Blob Storage**: almacenamiento de archivos y objetos.
- **Azure Data Lake Storage Gen2**: almacenamiento orientado al análisis masivo de datos.
- **Azure Files**: recursos compartidos de archivos accesibles desde distintos sistemas operativos.

Durante el desarrollo del laboratorio se analizarán las características principales de cada servicio y las diferencias entre ellos.

---

# 2. Objetivos

Los objetivos de esta práctica son:

- Crear una cuenta de almacenamiento en Azure.
- Comprender la estructura de los recursos de almacenamiento.
- Trabajar con contenedores y blobs.
- Analizar el funcionamiento de carpetas virtuales y carpetas jerárquicas.
- Habilitar Azure Data Lake Storage Gen2.
- Crear y gestionar recursos compartidos de archivos en Azure Files.
- Eliminar correctamente los recursos utilizados.

---

# 3. Creación de una Cuenta de Azure Storage

## Paso 1. Acceso al Portal de Azure

Acceder al Portal de Azure mediante una cuenta con permisos administrativos.

![Portal de Azure](IMG/1.png)

### Explicación

El Portal de Azure es la interfaz web que permite crear y administrar todos los recursos de la plataforma cloud de Microsoft.

---

## Paso 2. Crear un nuevo recurso

Seleccionar:

**Create a Resource → Storage Account**

![Crear recurso](IMG/2.png)

---

## Paso 3. Configuración básica

Introducir los siguientes parámetros:

| Configuración | Valor |
|--------------|--------|
| Subscription | Suscripción personal |
| Resource Group | dp900-lab-rg |
| Storage Account Name | Nombre único |
| Region | Región más cercana |
| Performance | Standard |
| Redundancy | Locally-redundant storage (LRS) |

![Configuración básica](IMG/3.png)

### Explicación

- **Resource Group:** agrupa recursos relacionados.
- **Standard:** opción económica para pruebas y laboratorios.
- **LRS:** mantiene tres copias de los datos dentro de una misma región.

---

## Paso 4. Configuración avanzada

En la pestaña **Advanced**, comprobar que la opción:

**Enable Hierarchical Namespace**

permanece desactivada.

![Configuración avanzada](IMG/4.png)

### Explicación

Inicialmente trabajaremos con Blob Storage tradicional para comprender el funcionamiento de las carpetas virtuales.

---

## Paso 5. Protección de datos

Desactivar todas las opciones relacionadas con:

- Soft Delete para blobs.
- Soft Delete para contenedores.
- Soft Delete para recursos compartidos.

![Protección de datos](IMG/5.png)

---

## Paso 6. Validación y despliegue

Revisar la configuración y seleccionar **Create**.

Una vez finalizado el despliegue, acceder al recurso creado.

![Despliegue completado](IMG/6.png)

---

# 4. Exploración de Azure Blob Storage

## Paso 1. Crear un contenedor

Acceder a:

**Data Storage → Containers**

Crear un nuevo contenedor denominado:

`data`

![Crear contenedor](IMG/7.png)

### Explicación

Un contenedor es la unidad lógica donde se almacenan los blobs dentro de una cuenta de almacenamiento.

---

## Paso 2. Verificar el contenedor

Comprobar que el contenedor aparece correctamente en la lista.

![Contenedor creado](IMG/8.png)

---

## Paso 3. Acceder al Storage Browser

Entrar en:

**Storage Browser → Blob Containers → data**

Verificar que el contenedor se encuentra vacío.

![Storage Browser](IMG/9.png)

---

## Paso 4. Crear un directorio virtual

Seleccionar:

**Add Directory**

Nombre:

`products`

![Crear directorio](IMG/10.png)

---

## Paso 5. Comprobar el comportamiento de carpetas virtuales

Regresar al contenedor principal y observar que la carpeta desaparece al no contener archivos.

![Carpetas virtuales](IMG/11.png)

### Explicación

Azure Blob Storage utiliza una estructura plana.

Las carpetas son únicamente rutas lógicas y no existen físicamente hasta que contienen algún archivo.

---

## Paso 6. Subir un archivo JSON

Descargar previamente:

`product1.json`

Subir el archivo indicando:

**Upload to folder:**

`product_data`

![Subida de archivo](IMG/12.png)

---

## Paso 7. Verificar la carga

Comprobar que aparece la carpeta virtual:

`product_data`

y dentro de ella el archivo:

`product1.json`

![Archivo cargado](IMG/13.png)

---

## Resultado obtenido

Se ha comprobado el funcionamiento de Azure Blob Storage utilizando carpetas virtuales dentro de una estructura de almacenamiento plana.

---

# 5. Exploración de Azure Data Lake Storage Gen2

## Paso 1. Descargar el segundo archivo

Descargar:

`product2.json`

para utilizarlo posteriormente.

---

## Paso 2. Habilitar Data Lake Gen2

Acceder a:

**Settings → Data Lake Gen2 Upgrade**

Completar los tres pasos del asistente.

![Upgrade Gen2](IMG/14.png)

### Explicación

Esta actualización activa el uso de un espacio de nombres jerárquico que permite gestionar directorios reales.

---

## Paso 3. Verificar los datos existentes

Comprobar que el archivo:

`product1.json`

continúa disponible tras la actualización.

![Verificación datos](IMG/15.png)

---

## Paso 4. Subir un nuevo archivo

Subir:

`product2.json`

a la carpeta:

`product_data`

![Subir segundo archivo](IMG/16.png)

---

## Paso 5. Verificar ambos archivos

Confirmar que aparecen:

- product1.json
- product2.json

![Archivos almacenados](IMG/17.png)

---

## Paso 6. Analizar las nuevas capacidades

Abrir el menú contextual de la carpeta.

Ahora aparecen opciones como:

- Rename
- Delete
- Manage ACL
- Generate SAS

![Opciones ACL](IMG/18.png)

### Explicación

Con Data Lake Storage Gen2 las carpetas pasan a existir físicamente dentro de la estructura del almacenamiento.

Esto permite:

- Gestionar permisos.
- Renombrar carpetas.
- Aplicar ACL.
- Organizar grandes volúmenes de información.

---

## Resultado obtenido

Se ha observado la diferencia entre una estructura plana y una estructura jerárquica de almacenamiento.

---

# 6. Exploración de Azure Files

## Paso 1. Acceder a Classic File Shares

Dentro de la cuenta de almacenamiento acceder a:

**Data Storage → Classic File Shares**

![Azure Files](IMG/19.png)

---

## Paso 2. Crear un recurso compartido

Seleccionar:

**+ Classic File Share**

Configuración:

| Parámetro | Valor |
|------------|---------|
| Name | files |
| Access Tier | Transaction Optimized |

![Crear File Share](IMG/20.png)

---

## Paso 3. Desactivar Backup

Desmarcar la opción:

**Enable Backup**

![Backup desactivado](IMG/21.png)

---

## Paso 4. Crear el recurso

Seleccionar:

**Review + Create → Create**

![Crear recurso compartido](IMG/22.png)

---

## Paso 5. Conexión al recurso compartido

Abrir el recurso creado y seleccionar:

**Connect**

Observar los scripts disponibles para:

- Windows
- Linux
- macOS

![Conexión File Share](IMG/23.png)

### Explicación

Azure Files permite compartir carpetas mediante protocolos estándar como SMB y NFS, facilitando la integración con servidores y equipos locales.

---

## Resultado obtenido

Se ha creado y configurado correctamente un recurso compartido de archivos en Azure.

---

# 7. Limpieza de Recursos

Para evitar costes innecesarios se procede a eliminar todos los recursos creados.

## Paso 1

Acceder al grupo de recursos:

`dp900-lab-rg`

---

## Paso 2

Seleccionar:

**Delete Resource Group**

Introducir el nombre del grupo para confirmar la eliminación.

![Eliminar Resource Group](IMG/24.png)

---

# 8. Conclusiones

Durante esta práctica se han explorado los principales servicios de almacenamiento no relacional de Microsoft Azure.

Los resultados obtenidos permiten concluir que:

- Azure Blob Storage es adecuado para almacenar grandes cantidades de archivos y datos no estructurados.
- Azure Data Lake Storage Gen2 proporciona capacidades avanzadas para análisis de datos y gestión jerárquica.
- Azure Files facilita la compartición de archivos utilizando protocolos tradicionales compatibles con múltiples sistemas operativos.
- La utilización de Resource Groups simplifica enormemente la administración y eliminación de recursos.

En conjunto, estos servicios constituyen la base del almacenamiento de datos no relacionales dentro del ecosistema Microsoft Azure.
