# Práctica de Laboratorio: Exploración de Azure Storage


# Resumen

En esta práctica se ha realizado la creación y configuración de una cuenta de almacenamiento en Microsoft Azure con el objetivo de explorar los principales servicios de almacenamiento no relacional.

Se han analizado tres servicios fundamentales: **Azure Blob Storage**, **Azure Data Lake Storage Gen2** y **Azure Files**, comprendiendo sus diferencias, funcionamiento y casos de uso.

Además, se ha estudiado la diferencia entre estructuras de almacenamiento planas y jerárquicas, así como los mecanismos de acceso, organización y seguridad de los datos en la nube.

---

# 1. Introducción

Microsoft Azure Storage es una solución de almacenamiento en la nube altamente escalable, segura y disponible. Permite almacenar datos no estructurados como archivos, imágenes, documentos o grandes volúmenes de información analítica.

A diferencia de las bases de datos relacionales, este tipo de almacenamiento no requiere una estructura fija de tablas, lo que lo hace ideal para escenarios de Big Data, aplicaciones web y sistemas distribuidos.

---

# 2. Objetivos

Los objetivos principales de esta práctica son:

- Crear una cuenta de almacenamiento en Microsoft Azure.
- Comprender la arquitectura de Azure Storage.
- Trabajar con Azure Blob Storage.
- Analizar el comportamiento de carpetas virtuales.
- Activar y utilizar Azure Data Lake Storage Gen2.
- Comprender el concepto de directorios jerárquicos.
- Crear y configurar Azure Files.
- Comparar los distintos servicios de almacenamiento.
- Eliminar recursos para evitar costes innecesarios.

---

# 3. Arquitectura del laboratorio

La infraestructura utilizada en esta práctica se basa en una única cuenta de almacenamiento sobre la que se despliegan diferentes servicios:

```
Azure Storage Account
│
├── Blob Storage
│   └── Contenedor: data
│       └── product_data
│           ├── product1.json
│           └── product2.json
│
├── Data Lake Storage Gen2
│   └── Espacio de nombres jerárquico habilitado
│
└── Azure Files
    └── File Share: files
```

---

# 4. Creación de la cuenta de almacenamiento

## Paso 1. Acceso al portal de Azure

Accedemos al portal de Azure desde un navegador web.

**Figura 1. Portal de Azure**

![Portal Azure](IMG/1.png)

**Análisis:**  
El portal de Azure es la interfaz principal de administración de recursos en la nube.

---

## Paso 2. Creación del recurso

Se selecciona la opción **Storage Account** dentro de “Create a resource”.

**Figura 2. Creación de Storage Account**

![Crear recurso](IMG/2.png)

---

## Paso 3. Configuración básica

Se establecen los siguientes parámetros:

| Parámetro | Valor |
|----------|------|
| Resource Group | dp900-lab-rg |
| Performance | Standard |
| Redundancy | LRS |

**Figura 3. Configuración básica**

![Configuración](IMG/3.png)

**Análisis:**  
Se utiliza configuración estándar para optimizar costes en entorno de laboratorio.

---

## Paso 4. Configuración avanzada

Se mantiene desactivada la opción **Hierarchical Namespace**.

**Figura 4. Configuración avanzada**

![Avanzado](IMG/4.png)

---

## Paso 5. Protección de datos

Se desactivan opciones de soft delete.

**Figura 5. Protección de datos**

![Protección](IMG/5.png)

---

## Paso 6. Creación del recurso

Se valida la configuración y se despliega la cuenta.

**Figura 6. Recurso creado**

![Deploy](IMG/6.png)

---

# 5. Azure Blob Storage

## Paso 1. Creación del contenedor

Se crea un contenedor llamado `data`.

**Figura 7. Contenedor creado**

![Contenedor](IMG/7.png)

---

## Paso 2. Verificación

El contenedor aparece correctamente en la lista.

**Figura 8. Verificación**

![Verificación](IMG/8.png)

---

## Paso 3. Storage Browser

Se accede al explorador de almacenamiento.

**Figura 9. Storage Browser**

![Browser](IMG/9.png)

---

## Paso 4. Directorio virtual

Se crea la carpeta `products`.

**Figura 10. Directorio virtual**

![Directorio](IMG/10.png)

---

## Paso 5. Comportamiento de carpetas

La carpeta desaparece al no contener archivos.

**Figura 11. Carpeta virtual**

![Virtual](IMG/11.png)

**Análisis:**  
Azure Blob Storage utiliza una estructura plana basada en nombres, no directorios reales.

---

## Paso 6. Subida de archivo

Se sube `product1.json` al contenedor.

**Figura 12. Subida de archivo**

![Upload](IMG/12.png)

---

## Paso 7. Resultado

Se verifica la existencia del archivo en `product_data`.

**Figura 13. Resultado**

![Resultado](IMG/13.png)

---

# 6. Azure Data Lake Storage Gen2

## Paso 1. Archivo adicional

Se descarga `product2.json`.

---

## Paso 2. Activación de Gen2

Se habilita el espacio de nombres jerárquico.

**Figura 14. Upgrade Gen2**

![Gen2](IMG/14.png)

---

## Paso 3. Verificación

Se comprueba la persistencia de datos.

**Figura 15. Verificación**

![Check](IMG/15.png)

---

## Paso 4. Nuevo archivo

Se sube `product2.json`.

**Figura 16. Upload 2**

![Upload2](IMG/16.png)

---

## Paso 5. Resultados

Ambos archivos están disponibles.

**Figura 17. Archivos**

![Files](IMG/17.png)

---

## Paso 6. Nuevas funcionalidades

Opciones avanzadas como ACL y Rename están disponibles.

**Figura 18. ACL**

![ACL](IMG/18.png)

**Análisis:**  
Ahora los directorios son reales y permiten gestión avanzada de permisos.

---

# 7. Azure Files

## Paso 1. File Share

Se accede a Classic File Shares.

**Figura 19. Azure Files**

![Files](IMG/19.png)

---

## Paso 2. Creación

Se crea el recurso `files`.

**Figura 20. Crear share**

![Share](IMG/20.png)

---

## Paso 3. Backup

Se desactiva backup.

**Figura 21. Backup**

![Backup](IMG/21.png)

---

## Paso 4. Creación final

Se despliega el recurso.

**Figura 22. Creado**

![Create](IMG/22.png)

---

## Paso 5. Conexión

Se visualizan scripts de conexión.

**Figura 23. Connect**

![Connect](IMG/23.png)

**Análisis:**  
Permite acceso mediante SMB/NFS desde distintos sistemas operativos.

---

# 8. Aprendizajes obtenidos

- Creación de cuentas de almacenamiento en Azure.
- Gestión de contenedores y blobs.
- Diferencias entre estructuras planas y jerárquicas.
- Uso de Azure Data Lake Storage Gen2.
- Aplicación de ACL en almacenamiento.
- Creación de Azure Files.
- Eliminación de recursos en Azure.

---

# 9. Conclusiones

Esta práctica ha permitido comprender de forma completa el funcionamiento de los principales servicios de almacenamiento de Microsoft Azure.

Se ha observado cómo Azure Blob Storage utiliza una estructura basada en objetos con carpetas virtuales, mientras que Azure Data Lake Storage Gen2 introduce una jerarquía real que mejora la organización y el control de datos.

Por otro lado, Azure Files proporciona una solución compatible con sistemas de archivos tradicionales, facilitando la migración de aplicaciones locales a la nube.

En conjunto, estos servicios demuestran la flexibilidad de Azure para adaptarse a diferentes escenarios de almacenamiento, desde aplicaciones simples hasta sistemas de análisis de Big Data.

---

# 10. Limpieza de recursos

Se elimina el grupo de recursos para evitar costes.

**Figura 24. Eliminación**

![Delete](IMG/24.png)

---
