# 📊 Laboratorio: Microsoft Fabric - Análisis de datos

## 🧠 Descripción
En este laboratorio utilizamos Microsoft Fabric para crear un Workspace, un Lakehouse, cargar datos del dataset NYC Taxi, consultarlos con SQL y eliminar recursos.

# 🚀 PASO A PASO

## 1️⃣ Acceder a Microsoft Fabric
Entra en:
https://app.fabric.microsoft.com/home?experience=fabric  
Inicia sesión y asegúrate de estar en la experiencia Fabric.

📸 ![Paso 1](IMGL1/1.png)

📸 ![Paso 2](IMGL1/2.png)

## 2️⃣ Crear Workspace
- Ve a Workspaces  
- New workspace  
- Nombre: dp900-fabric-lakehouse  

📸 ![Paso 2](IMGL1/3.png)

📸 ![Paso 3](IMGL1/4.png)

- Como muestra esta vacio

📸 ![Paso 3](IMGL1/5.png)

## 3️⃣ Crear Lakehouse
- New item  
- Lakehouse  
- Nombre: taxi_lakehouse  

📸 ![Paso 4](IMGL1/6.png)

📸 ![Paso 4](IMGL1/7.png)

📸 ![Paso 4](IMGL1/8.png)

## 4️⃣ Ingesta de datos (Copy Job)

📸 ![Paso 4](IMGL1/9.png)

- Get data → New copy job  
- Dataset: NYC Taxi - Green  
- Nombre: Ingest Data  

Configuración:
- Full copy  
- Tables  
- dbo  
- taxi_rides  

📸 ![Paso 4](IMGL1/10.png)

📸 ![Paso 4](IMGL1/11.png)

📸 ![Paso 4](IMGL1/12.png)

📸 ![Paso 4](IMGL1/13.png)

📸 ![Paso 4](IMGL1/14.png)

📸 ![Paso 4](IMGL1/15.png)

📸 ![Paso 4](IMGL1/16.png)

La copia a funcionado, por lo que esperamos que muestre tablas completada u exitoso 

📸 ![Paso 4](IMGL1/17.png)

## 📂 5️⃣ Exploración de datos en el Lakehouse

Una vez cargados los datos en el Lakehouse, podemos acceder a la tabla para revisarlos y validar que la ingesta se realizó correctamente.

---

### 👀 Visualización de datos

En esta sección puedes explorar el contenido de la tabla directamente desde Microsoft Fabric.

📸 Captura:

![Paso 5](IMGL1/18.png)

---

### 💡 Nota

Esta tabla contiene los datos del dataset NYC Taxi, que posteriormente se utilizarán en consultas SQL para análisis.

## 📊 6️⃣ Consulta de datos en el Lakehouse (SQL)

Ahora que los datos ya están cargados en la tabla del Lakehouse, podemos analizarlos utilizando SQL.

💡 **Consejo:** Las tablas de un Lakehouse son totalmente compatibles con SQL, lo que permite analizar los datos sin moverlos a otro sistema.

![Paso 5](IMGL1/19.png)

---

### 🚀 Acceder al endpoint SQL

En la parte superior derecha del Lakehouse:

- Selecciona **Analizar datos con**
- Luego selecciona **Endpoint de análisis SQL**

💡 Este endpoint está optimizado para ejecutar consultas SQL sobre las tablas del Lakehouse y se integra con herramientas de análisis conocidas.

---

### 🧾 Ejecutar consulta SQL

En la barra de herramientas:

- Selecciona **Nueva consulta SQL**
- Copia y ejecuta la siguiente consulta:

```sql
SELECT  
    DATENAME(dw, lpepPickupDatetime) AS Day,
    AVG(tripDistance) AS AvgDistance
FROM taxi_rides
GROUP BY DATENAME(dw, lpepPickupDatetime)
```


![Paso 5](IMGL1/20.png)

## 🧹 7️⃣ Limpieza de recursos

Si has terminado de explorar Microsoft Fabric, puedes eliminar el espacio de trabajo que creaste para este ejercicio.

💡 **Consejo:** Eliminar el espacio de trabajo elimina todos los elementos creados en el laboratorio y ayuda a evitar cargos continuos.

---

### 📌 Pasos para eliminar el workspace:

1. En la barra lateral izquierda, selecciona el icono de tu espacio de trabajo para ver todos los elementos que contiene.  

2. En la barra de herramientas, selecciona **Configuración del espacio de trabajo**.  

3. En la sección **General**, selecciona **Eliminar este espacio de trabajo**.  

---

📸 Añade aquí capturas del proceso:

- Workspace abierto  
  ![Paso 7 - 1](IMGL1/21.png)

- Configuración del workspace  
  ![Paso 7 - 2](IMGL1/22.png)

