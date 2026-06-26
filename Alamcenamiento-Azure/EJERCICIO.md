# 📘 Actividad 3.1 — OneLake en Microsoft Fabric

## 🌊 ¿Qué es OneLake?

OneLake es el sistema de almacenamiento unificado de Microsoft Fabric. Se trata de un **data lake lógico global y centralizado** que actúa como capa única de almacenamiento para todos los servicios del ecosistema (Data Factory, Lakehouse, Warehouse, Real-Time Analytics y Power BI).

Su principal objetivo es eliminar la fragmentación del dato y permitir una arquitectura **data-driven unificada sin duplicación de información**.

---

## ❓ ¿Es un data lake?

Sí. OneLake es un data lake, pero evolucionado respecto a los modelos tradicionales.

Permite:
- Almacenamiento de datos estructurados, semiestructurados y no estructurados
- Acceso compartido entre todos los servicios de Fabric
- Eliminación de duplicidad mediante “shortcuts”
- Integración directa con analítica, ingeniería de datos y BI

---

## 🔗 Relación con ADLS Gen2

OneLake está construido sobre la base tecnológica de Azure Data Lake Storage Gen2 (ADLS Gen2), pero no es simplemente una instancia de este.

- ADLS Gen2 → almacenamiento de objetos en Azure
- OneLake → capa superior de abstracción, gobernanza y unificación global

---

## ⚖️ Similitudes

- Arquitectura de data lake basada en almacenamiento de objetos
- Escalabilidad masiva
- Soporte de múltiples formatos de datos
- Integración con motores analíticos

---

## ❗ Diferencias clave

- OneLake es un **data lake único a nivel organizacional**
- ADLS Gen2 es un servicio de almacenamiento independiente
- OneLake permite acceso sin copia de datos (shortcuts)
- OneLake está integrado de forma nativa en todo Microsoft Fabric
- OneLake incorpora gobernanza y acceso unificado multi-servicio

---

## 🧾 Conclusión

OneLake representa la evolución del data lake tradicional hacia un modelo unificado, eliminando silos de datos y simplificando la arquitectura analítica moderna.

---

# 📘 Actividad 3.2 — Equivalente de Azure Data Factory en Microsoft Fabric

## 🔷 ¿Qué es Data Factory en Fabric?

Data Factory en Microsoft Fabric es el componente encargado de la **ingestión, transformación y orquestación de datos** dentro de la plataforma.

Permite crear pipelines que conectan múltiples fuentes de datos tanto internas como externas al ecosistema Fabric.

---

## ❓ ¿Es lo mismo que Azure Data Factory (ADF)?

No. No es lo mismo, aunque comparten base conceptual.

- Azure Data Factory → servicio independiente de integración de datos en Azure
- Fabric Data Factory → componente nativo dentro de una plataforma unificada de datos y analítica

---

## 🔎 Similitudes

- Diseño de pipelines ETL/ELT
- Amplio catálogo de conectores
- Orquestación de procesos de datos
- Integración con fuentes cloud y on-premise
- Enfoque low-code/no-code

---

## ⚠️ Diferencias clave

| Azure Data Factory (ADF) | Fabric Data Factory |
|--------------------------|---------------------|
| Servicio independiente | Servicio integrado en Fabric |
| Orientado a integración de datos | Orientado a analítica unificada |
| Arquitectura modular | Arquitectura centralizada |
| Uso combinado con otros servicios Azure | Uso nativo de OneLake |
| Mayor madurez | Plataforma más reciente |

---

## ☁️ Conectividad multi-cloud

Fabric Data Factory permite integración con distintos entornos:

- Azure (SQL, Storage, Synapse, etc.)
- AWS (S3, servicios mediante conectores)
- GCP (BigQuery mediante conectores)
- APIs REST, ODBC y JDBC

---

## 🎯 Utilidad

- Integración de datos multi-cloud
- Eliminación de silos de información
- Arquitecturas híbridas
- Centralización del dato en Fabric
- Alimentación de analítica avanzada y BI

---

## 🧾 Conclusión

Fabric Data Factory no sustituye completamente a Azure Data Factory, sino que lo evoluciona dentro de una plataforma unificada de datos, analítica y gobierno del dato.

---

# 📘 Actividad 3.3 — Equivalentes entre Azure, AWS, GCP y Fabric

## 📌 1. Bases de datos relacionales

| Azure | AWS | GCP | Microsoft Fabric |
|------|-----|-----|------------------|
| Azure SQL Database | Amazon RDS / Aurora | Cloud SQL / AlloyDB | Fabric Warehouse (SQL endpoint) |

---

## 📌 2. Integración y orquestación de datos

| Azure | AWS | GCP | Microsoft Fabric |
|------|-----|-----|------------------|
| Azure Data Factory | AWS Glue | Cloud Data Fusion / Dataflow | Fabric Data Factory |

---

## 📌 3. Almacenamiento tipo Data Lake

| Azure | AWS | GCP | Microsoft Fabric |
|------|-----|-----|------------------|
| ADLS Gen2 | Amazon S3 | Google Cloud Storage | OneLake |

---

## 🧠 Resumen de servicios equivalentes

### 🔷 AWS

- Amazon RDS / Aurora → bases de datos relacionales gestionadas
- AWS Glue → servicio serverless de integración de datos (ETL/ELT)
- Amazon S3 → almacenamiento de objetos usado para data lakes

---

### 🔷 GCP

- Cloud SQL / AlloyDB → bases de datos relacionales gestionadas
- Dataflow / Data Fusion → procesamiento e integración de datos
- Google Cloud Storage → almacenamiento escalable tipo data lake

---

### 🔷 Microsoft Fabric

- Fabric Warehouse → motor analítico SQL integrado
- Fabric Data Factory → orquestación e integración de datos
- OneLake → data lake unificado global de toda la plataforma

---

## 🧾 Conclusión general

AWS y GCP utilizan arquitecturas basadas en múltiples servicios especializados, mientras que Microsoft Fabric apuesta por un modelo unificado donde almacenamiento, integración, analítica y visualización están centralizados en una sola plataforma.
