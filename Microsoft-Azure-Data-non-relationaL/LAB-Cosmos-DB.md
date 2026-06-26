# Práctica de Laboratorio: Exploración de Azure Cosmos DB

---

# Resumen

En esta práctica se ha creado y configurado una base de datos NoSQL en Microsoft Azure utilizando Azure Cosmos DB.

Se ha trabajado con datos en formato JSON, realizando inserción de elementos, visualización de documentos y ejecución de consultas mediante un lenguaje SQL simplificado.

El objetivo principal ha sido comprender el funcionamiento de bases de datos NoSQL en la nube y su diferencia respecto a los modelos relacionales tradicionales.

---

# 1. Introducción

Azure Cosmos DB es un servicio de base de datos NoSQL completamente administrado por Microsoft Azure, diseñado para almacenar y consultar datos en formato JSON de manera escalable y distribuida.

A diferencia de las bases de datos relacionales, Cosmos DB no requiere una estructura fija de tablas, lo que permite una mayor flexibilidad en el almacenamiento de datos.

Este servicio es especialmente útil en aplicaciones modernas, sistemas distribuidos, aplicaciones web y escenarios de análisis en tiempo real.

---

# 2. Objetivos

Los objetivos de esta práctica son:

- Crear una cuenta de Azure Cosmos DB.
- Comprender el concepto de bases de datos NoSQL.
- Crear bases de datos y contenedores.
- Insertar documentos en formato JSON.
- Explorar la estructura interna de los datos.
- Ejecutar consultas SQL sobre datos NoSQL.
- Comprender el concepto de clave de partición.
- Eliminar los recursos creados para evitar costes.

---

# 3. Arquitectura del laboratorio

La arquitectura utilizada en esta práctica se basa en un único recurso principal:

```
Azure Cosmos DB Account
│
└── SampleDB
    └── SampleContainer
        ├── Item 1 (JSON)
        ├── Item 2 (JSON)
        └── Item 3 (JSON)
```

---

# 4. Creación de la cuenta de Azure Cosmos DB

## Paso 1. Acceso al portal de Azure

Se accede al portal de Azure desde el navegador web.

**Figura 1. Portal de Azure**

![Portal Azure](IMG/1.png)

**Análisis:**  
El portal de Azure es el centro de administración de todos los servicios cloud.

---

## Paso 2. Creación del recurso

Se selecciona:

**Azure Cosmos DB → Create**

**Figura 2. Creación de Cosmos DB**

![Crear Cosmos DB](IMG/2.png)

---

## Paso 3. Configuración básica

Se introducen los siguientes parámetros:

| Parámetro | Valor |
|----------|------|
| Workload | Learning |
| API | NoSQL |
| Resource Group | Grupo existente |
| Account Name | Único |
| Location | Región cercana |
| Capacity Mode | Provisioned throughput |

**Figura 3. Configuración inicial**

![Configuración](IMG/3.png)

**Análisis:**  
Se utiliza el modo Learning para optimizar costes y simplificar la configuración.

---

## Paso 4. Validación y despliegue

Se revisa la configuración y se crea la cuenta.

**Figura 4. Validación**

![Deploy](IMG/4.png)

---

# 5. Creación de base de datos y contenedor

## Paso 1. Data Explorer

Se accede a la sección **Data Explorer**.

**Figura 5. Data Explorer**

![Explorer](IMG/5.png)

---

## Paso 2. Quick Start

Se selecciona **Launch Quick Start** para crear automáticamente:

- Base de datos: SampleDB  
- Contenedor: SampleContainer  
- Clave de partición: /categoryId  

**Figura 6. Quick Start**

![Quick start](IMG/6.png)

---

## Paso 3. Concepto de clave de partición

La clave de partición permite distribuir los datos en diferentes nodos para mejorar el rendimiento y la escalabilidad.

En este caso se utiliza:

`/categoryId`

---

# 6. Inserción y visualización de datos

## Paso 1. Visualización de items

Se accede a la sección **Items** del contenedor.

**Figura 7. Items**

![Items](IMG/7.png)

---

## Paso 2. Inserción de un nuevo documento

Se crea un nuevo elemento JSON:

```json
{
    "name": "Road Helmet,45",
    "id": "123456789",
    "categoryId": "123456789",
    "SKU": "AB-1234-56",
    "description": "The product called \"Road Helmet,45\" ",
    "price": 48.74
}
```

**Figura 8. Inserción de JSON**

![Insert](IMG/8.png)

---

## Paso 3. Resultado

Tras guardar el documento, Cosmos DB añade automáticamente metadatos internos como:

- `_rid`
- `_etag`
- `_ts`
- `_self`

---

# 7. Consultas SQL en Azure Cosmos DB

## Paso 1. Consulta básica

Se ejecuta la consulta:

```sql
SELECT * FROM c
```

**Figura 9. Query básica**

![Query1](IMG/9.png)

---

## Paso 2. Consulta filtrada

Se modifica la consulta:

```sql
SELECT *
FROM c
WHERE CONTAINS(c.name, "Helmet")
```

**Figura 10. Query filtrada**

![Query2](IMG/10.png)

---

## Análisis

Cosmos DB permite realizar consultas SQL sobre datos NoSQL, lo que facilita la búsqueda y filtrado de información sin necesidad de estructuras complejas.

---

# 8. Aprendizajes obtenidos

- Creación de bases de datos NoSQL en Azure.
- Uso de Azure Cosmos DB.
- Inserción de documentos JSON.
- Concepto de esquema flexible (schema-less).
- Uso de claves de partición.
- Ejecución de consultas SQL sobre datos NoSQL.
- Visualización de metadatos automáticos.

---

# 9. Conclusiones

Esta práctica ha permitido comprender el funcionamiento de las bases de datos NoSQL utilizando Azure Cosmos DB.

Se ha comprobado cómo los datos se almacenan en formato JSON, permitiendo una estructura flexible sin necesidad de esquemas rígidos.

Además, se ha observado cómo Cosmos DB proporciona un lenguaje de consultas similar a SQL, facilitando la transición desde bases de datos relacionales.

Finalmente, se concluye que Azure Cosmos DB es una solución altamente escalable, flexible y adecuada para aplicaciones modernas que requieren alto rendimiento y distribución global.

---

# 10. Limpieza de recursos

Se elimina el grupo de recursos para evitar costes adicionales.

**Figura 11. Eliminación de recursos**

![Delete RG](IMG/11.png)

---

# Fin de la práctica
