# Diseñar e implementar un modelo dimensional en Microsoft Fabric

## Objetivo

El objetivo de este laboratorio es diseñar e implementar un modelo dimensional basado en un esquema en estrella utilizando Microsoft Fabric. Para ello, se crea un almacén de datos, se definen las tablas de hechos y dimensiones, se establecen las relaciones entre ellas, se cargan datos de ejemplo y se realizan consultas analíticas. Además, se implementan patrones Slowly Changing Dimension (SCD) de tipo 1 y tipo 2 para gestionar cambios históricos en los datos.

---

# 1. Crear el espacio de trabajo

Se crea un nuevo espacio de trabajo en Microsoft Fabric que servirá como entorno donde se almacenarán todos los recursos utilizados durante la práctica.

### Pasos
- Acceder a Microsoft Fabric.
- Crear un nuevo Workspace.
- Seleccionar una capacidad Fabric o de prueba.

📷 **Captura 1:** Workspace creado.

---

# 2. Crear el Warehouse

Dentro del espacio de trabajo se crea un nuevo almacén de datos llamado **ContosoDW**, que será el encargado de almacenar el modelo dimensional.

### Pasos
- Pulsar **Nuevo elemento**.
- Seleccionar **Warehouse**.
- Asignar el nombre **ContosoDW**.
- Esperar a que finalice la creación.

📷 **Captura 2:** Warehouse creado.

---

# 3. Crear la tabla de hechos

Se crea la tabla **f_Sales**, encargada de almacenar las transacciones de venta. Esta tabla contiene las medidas del negocio y las claves que la relacionan con las dimensiones.

```sql
CREATE TABLE f_Sales
(
    DateKey INT NOT NULL,
    StoreKey INT NOT NULL,
    ProductKey INT NOT NULL,
    CustomerKey INT NOT NULL,
    Quantity INT NOT NULL,
    UnitPrice DECIMAL(10,2) NOT NULL,
    SalesAmount DECIMAL(10,2) NOT NULL,
    DiscountAmount DECIMAL(10,2) NOT NULL
);
```

Ejecutar la consulta y comprobar que la tabla aparece en **dbo > Tables**.

📷 **Captura 3:** Tabla **f_Sales** creada.

---

# 4. Crear las tablas de dimensiones

Se crean las tablas **d_Date**, **d_Store**, **d_Product** y **d_Customer**, que proporcionan la información descriptiva necesaria para el análisis de las ventas.

### Pasos
- Crear una nueva consulta SQL.
- Ejecutar el script de creación de las cuatro dimensiones.
- Verificar que aparecen en el explorador.

📷 **Captura 4:** Tablas de dimensiones creadas.

---

# 5. Agregar las restricciones

Se añaden las claves primarias y las claves foráneas para establecer las relaciones entre la tabla de hechos y las dimensiones, formando el esquema en estrella.

📷 **Captura 5:** Restricciones creadas correctamente.

---

# 6. Cargar los datos

Se insertan datos de ejemplo en todas las tablas para poder realizar consultas y comprobar el funcionamiento del modelo dimensional.

📷 **Captura 6:** Datos cargados.

---

# 7. Consultar el esquema en estrella

Se ejecutan consultas SQL para analizar las ventas por categoría de producto, periodo de tiempo, región y segmento de cliente, comprobando que las relaciones entre las tablas funcionan correctamente.

📷 **Captura 7:** Resultado de las consultas.

---

# 8. Implementar SCD Tipo 2

Se simula un cambio en el coste de un producto. En lugar de modificar el registro existente, se crea una nueva versión del producto, manteniendo el histórico de cambios.

📷 **Captura 8:** Resultado del SCD Tipo 2.

---

# 9. Implementar SCD Tipo 1

Se corrige el nombre de un producto sobrescribiendo el valor anterior, sin conservar el historial.

📷 **Captura 9:** Resultado del SCD Tipo 1.

---

# 10. Verificar el modelo

Se ejecuta una consulta final uniendo la tabla de hechos con todas las dimensiones para comprobar que el modelo dimensional funciona correctamente y permite analizar la información desde diferentes perspectivas.

📷 **Captura 10:** Consulta final del modelo.

---

# Conclusión

Durante este laboratorio se ha implementado un modelo dimensional en Microsoft Fabric utilizando un esquema en estrella. Se han creado tablas de hechos y dimensiones, definido relaciones mediante claves primarias y foráneas, cargado datos de ejemplo y realizado consultas analíticas. Además, se han aplicado patrones SCD de tipo 1 y tipo 2 para gestionar cambios en los datos, obteniendo un modelo preparado para su explotación mediante herramientas de análisis como Power BI.
