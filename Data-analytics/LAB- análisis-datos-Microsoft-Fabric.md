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

## 5️⃣ Explorar datos
Ruta: Tables → dbo → taxi_rides  

📸 ![Paso 5](IMGL1/18.png)

## 6️⃣ Consulta SQL

📸 ![Paso 6](IMGL1/19.png)

```sql
SELECT  
    DATENAME(dw, lpepPickupDatetime) AS Day,
    AVG(tripDistance) AS AvgDistance
FROM taxi_rides
GROUP BY DATENAME(dw, lpepPickupDatetime)

📸 ![Paso 2](IMGL1/20.png)


## 6️⃣ Eliminación 

📸 ![Paso 7](IMGL1/21.png)

📸 ![Paso 7](IMGL1/22.png)
