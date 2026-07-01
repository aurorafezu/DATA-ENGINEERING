# 📊 Laboratorio: Fundamentos de visualización con Power BI

En este laboratorio, aprenderás a convertir datos en bruto en un informe interactivo utilizando Power BI Desktop, trabajando con la importación de datos, modelado y creación de visualizaciones.

---

## 1️⃣ Instalar Power BI Desktop
1. Descarga el instalador desde [https://aka.ms/power-bi-desktop](https://aka.ms/power-bi-desktop).
2. Ejecuta el asistente de configuración en tu equipo Windows.
                                                ![Paso 1](IMGL3/1.png)

---

## 2️⃣ Importar datos
Abre Power BI Desktop e importa los tres conjuntos de datos (clientes, productos y pedidos) mediante el conector Web:

1. Selecciona **Obtener datos** > **Web**.
2. Introduce la URL y pulsa **Conectar**:
   - Clientes: `https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/power-bi/customers.csv`
   - Productos: `https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/power-bi/products.csv`
   - Pedidos: `https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/power-bi/orders.csv`
3. Selecciona **Cargar** para cada archivo.

![Paso 2](IMGL3/2.png)
![Paso 3](IMGL3/3.png)
![Paso 4](IMGL3/4.png)
![Paso 5](IMGL3/5.png)
![Paso 6](IMGL3/6.png)
![Paso 7](IMGL3/7.png)

---

## 3️⃣ Explorar y refinar el modelo de datos
1. En el borde izquierdo, selecciona la **pestaña Modelo**.
![Paso 8](IMGL3/8.png)
2. En la tabla de **Pedidos**, selecciona el campo **Ingresos** y cambia su formato a **Moneda** en el panel de Propiedades.
![Paso 9](IMGL3/9.png)
3. En la tabla de **Productos**, haz clic derecho en **Categoría** > **Crear jerarquía**.
4. Añade **Nombreproducto** a esa jerarquía y renómbrala como **Producto Categorizado**.
![Paso 10](IMGL3/10.png)
![Paso 11](IMGL3/11.png)
![Paso 12](IMGL3/12.png)
5. En la vista de tabla, selecciona la columna **Ciudad** de la tabla **Clientes** y establece su *Categoría de datos* como **Ciudad**.
![Paso 13](IMGL3/13.png)
![Paso 14](IMGL3/14.png)

---

## 4️⃣ Crear el informe
1. Ve a **Archivo** > **Opciones y configuración** > **Opciones**. En **Seguridad**, activa **Usar Mapa y Visuales de Mapa Rellenado**.
![Paso 15](IMGL3/15.png)
2. Selecciona la pestaña **Vista de informe**.
![Paso 16](IMGL3/16.png)
3. Añade un **Cuadro de texto** con el título "Informe de Ventas" (fuente 32, negrita).
![Paso 17](IMGL3/17.png)
4. Selecciona el campo **Producto Categorizado** para crear una tabla y añade el campo **Ingresos**.
![Paso 18](IMGL3/18.png)
![Paso 19](IMGL3/19.png)
5. Cambia la visualización a **Gráfico de columnas apiladas**. Activa el icono de "desglose" (flecha hacia abajo) para explorar niveles.
![Paso 20](IMGL3/20.png)
![Paso 21](IMGL3/21.png)
6. Crea un nuevo gráfico con **Cantidad** (Pedidos) y **Categoría** (Productos) y cámbialo a **Gráfico circular**.
![Paso 22](IMGL3/22.png)
![Paso 23](IMGL3/23.png)
7. Crea un **Mapa** usando el campo **Ciudad** (Clientes) e **Ingresos** (Pedidos).
![Paso 24](IMGL3/24.png)
![Paso 25](IMGL3/25.png)

---

## 5️⃣ Guardar y finalizar
1. Prueba la interactividad haciendo clic en los elementos del mapa y observando cómo filtran el resto del informe.
2. Guarda tu trabajo como archivo `.pbix` desde el menú **Archivo** > **Guardar**.
![Paso 26](IMGL3/26.png)
