







--

# 🚀 Azure Cosmos DB 


# 🧠 1. Introducción

Las bases de datos relacionales son rígidas.

NoSQL permite:

- 📄 Documentos
- 🔑 Clave-valor
- 🕸️ Grafos
- 📊 Columnas

---

# ⚙️ 2. Arquitectura de Cosmos DB

## 🏗️ Estructura

1. Cuenta  
2. Base de datos  
3. Contenedor  
4. Items  

---

## 🖼️ Imagen arquitectura

![Arquitectura Cosmos DB](DOC/1.png)

---

# 🔑 3. Particiones (CLAVE DE EXAMEN)

- Divide datos en particiones lógicas
- Cada partición → 20 GB máximo
- Clave de partición = rendimiento

❌ Mala clave = hot partitions  
✔ Buena clave = escalabilidad

---

# 🌍 4. Distribución global

- Replicación automática
- Multi-región
- Baja latencia global

---

## 🖼️ Imagen global

![Distribución global](DOC/2.png)

---

# 📏 5. Consistencia

| Nivel | Descripción |
|------|-------------|
| 🔴 Fuerte | siempre actualizado |
| 🟠 Estancamiento acotado | retraso controlado |
| 🟡 Sesión | ⭐ recomendado |
| 🔵 Prefijo consistente | orden garantizado |
| ⚪ Eventual | alta disponibilidad |

---

# 💰 6. RU/s

- 1 RU ≈ lectura de 1 KB
- Todo consume RU

---

# ⚙️ 7. Modelos de rendimiento

| Modelo | Descripción |
|--------|-------------|
| 🟢 Dedicado | un contenedor |
| 🟡 Compartido | hasta 25 contenedores |
| 🔵 Serverless | pago por uso |

---

## 🖼️ Imagen rendimiento

![Rendimiento Cosmos DB](DOC/3.png)

---

# 🔌 8. APIs de Cosmos DB

:contentReference[oaicite:1]{index=1} soporta:

- NoSQL
- MongoDB
- Table
- Cassandra
- Gremlin

---

## 🖼️ Imagen APIs

![APIs Cosmos DB](DOC/4.png)

---

# 🕸️ 9. Gremlin (Grafos)

- Vértices = nodos
- Aristas = relaciones

---

## 🖼️ Imagen grafos

![Grafos Cosmos DB](DOC/5.png)

---

# 📌 10. Cuándo usar Cosmos DB

✔ IoT 📡  
✔ Gaming 🎮  
✔ E-commerce 🛒  
✔ Apps web/móviles 📱  

---

# ❌ 11. Cuándo NO usarlo

- ❌ JOINs complejos → Azure SQL Database
- ❌ Analítica histórica → Azure Synapse / Fabric

---

# 🧠 12. RESUMEN FINAL

:contentReference[oaicite:2]{index=2} es:

✔ Global  
✔ NoSQL  
✔ Multi-API  
✔ Escalable  
✔ Baja latencia  
✔ Basado en RU/s  

---
