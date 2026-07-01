# 📊 Laboratorio: Microsoft Fabric - Análisis en Tiempo Real

## 🧠 Descripción

En este laboratorio utilizamos **Microsoft Fabric** para trabajar con análisis en tiempo real.

Crearemos un flujo de datos (Eventstream), almacenaremos eventos en una Eventhouse y realizaremos consultas KQL para analizar datos en streaming.

---

# 🚀 PASO A PASO

---

## 1️⃣ Acceder a Microsoft Fabric

Accede a:

https://app.fabric.microsoft.com/home?experience=fabric

- Inicia sesión con tu cuenta
- Asegúrate de estar en la experiencia **Fabric**

📸 ![Paso 1](IMGL2/1.png)

---

## 2️⃣ Crear Workspace

- Ve a **Workspaces**
- Selecciona **New workspace**
- Nombre: `dp900-realtime`
- Selecciona capacidad (Trial / Fabric / Premium)

📸 ![Paso 2](IMGL2/2.png)

📸 Workspace creado:
![Paso 2](IMGL2/3.png)

---

## 3️⃣ Abrir Real-Time Hub

- En el menú izquierdo selecciona **Real-Time hub**
- Entra en **Data sources**

📸 ![Paso 3](IMGL2/4.png)

---

## 4️⃣ Conectar fuente de datos (Taxi Stream)

- Selecciona **Yellow Taxi Stream**
- Pulsa **Connect**
- Selecciona workspace: `dp900-realtime`
- Configura:
  - Source name: `taxi`
  - Eventstream name: `taxi-data-stream`

📸 ![Paso 4](IMGL2/5.png)

📸 Configuración:
![Paso 4](IMGL2/6.png)

---

## 5️⃣ Crear Eventstream

- Revisa la configuración
- Pulsa **Create eventstream**
- Espera a que el estado sea correcto

📸 ![Paso 5](IMGL2/7.png)

📸 Eventstream creado:
![Paso 5](IMGL2/8.png)

---

## 6️⃣ Crear Eventhouse (almacenamiento)

- En el Eventstream selecciona **Add destination**
- Elige **Eventhouse**
- Crear nuevo:
  - Eventhouse: `taxi-eventhouse`
  - Tabla: `yellow-taxi`
- Activar ingestión automática

📸 ![Paso 6](IMGL2/9.png)

📸 Configuración:
![Paso 6](IMGL2/10.png)

📸 Tabla creada:
![Paso 6](IMGL2/11.png)

---

## 7️⃣ Publicar flujo

- Pulsa **Publish**
- Espera a estado **Live**

📸 ![Paso 7](IMGL2/12.png)

📸 Flujo activo:
![Paso 7](IMGL2/13.png)

---

## 8️⃣ Ver datos en tiempo real

- Abre la Eventhouse
- Selecciona tabla `yellow-taxi`
- Ve a **Data preview**

📸 ![Paso 8](IMGL2/14.png)

📸 Datos en streaming:
![Paso 8](IMGL2/15.png)

---

## 🧹 10️⃣ Limpieza de recursos

En este ejercicio has creado un flujo de eventos en tiempo real, una Eventhouse y una base de datos KQL para analizar datos en streaming.

Si has terminado de explorar la Inteligencia en Tiempo Real de Microsoft Fabric, es recomendable eliminar los recursos creados.

💡 **Consejo:** Eliminar el espacio de trabajo borra automáticamente todos los elementos del laboratorio y evita posibles costes.

---

### 📌 Pasos para eliminar el workspace

1. En la barra lateral izquierda, selecciona el icono de **Workspaces** y abre tu espacio de trabajo `dp900-realtime`.

📸 ![Paso 10](IMGL2/20.png)

---

2. En la barra de herramientas, selecciona **Workspace settings**.

📸 ![Paso 10](IMGL2/21.png)

---

3. En la sección **General**, desplázate hacia abajo y selecciona **Delete this workspace**.

📸 ![Paso 10](IMGL2/22.png)

---

### ⚠️ Confirmación final

- Confirma la eliminación del workspace  
- Se eliminarán automáticamente:
  - Eventstream  
  - Eventhouse  
  - Base de datos KQL  
  - Tabla yellow-taxi  

---

## ✅ Resultado final

✔ Flujo en tiempo real creado  
✔ Datos ingeridos correctamente  
✔ Consultas KQL realizadas  
✔ Recursos eliminados correctamente  
