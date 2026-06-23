# 📥 Capa de Ingesta

## 🎯 Objetivo
Capturar, integrar y transportar datos desde múltiples fuentes hacia la plataforma analítica, garantizando seguridad, escalabilidad y confiabilidad.

---

## ⚙️ Funciones principales
- Captura de datos desde múltiples sistemas (BD, APIs, IoT, apps)
- Ingesta en tiempo real (streaming) y por lotes (batch)
- Gestión de eventos y mensajería
- Orquestación de flujos de datos
- Validación inicial de datos
- Trazabilidad del origen de la información

---

## 🌐 Tecnologías Open Source
- Apache Kafka
- Apache NiFi
- Airbyte
- Logstash
- Apache Flume

---

## 💰 Tecnologías de Pago
- Informatica PowerCenter
- Talend Data Integration
- Fivetran
- StreamSets
- Confluent Cloud

---

## ☁️ Azure / Microsoft
- Azure Data Factory
- Azure Event Hubs
- Azure Service Bus
- Azure Stream Analytics
- Azure IoT Hub

---

## 📝 Ejemplo Real (Caso de uso)
Una empresa global necesita integrar datos de diferentes sistemas:

- 🗄️ PostgreSQL → clientes y pedidos
- 💼 Salesforce → ventas y oportunidades
- 🌐 API externa → tipo de cambio
- 📡 IoT → sensores en tiempo real

👉 Flujo de ingestión:

- Apache Kafka o Azure Event Hubs reciben eventos en tiempo real  
- Azure Data Factory ejecuta cargas por lotes  
- Azure Service Bus gestiona colas de mensajes  
- Los datos se envían al Data Lake para su almacenamiento

---

## 🔑 Idea Clave
La capa de ingesta es el **puente crítico entre las fuentes de datos y la plataforma analítica**, asegurando que la información llegue de forma correcta, continua y sin pérdida de datos.
