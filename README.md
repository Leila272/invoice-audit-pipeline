Intelligent Document Processing (IDP) Pipeline 🚀

### Proyecto de Auditoría IT & Automatización de Procesos (I+D)

## 📌 Descripción General
eContratistas es una solución de automatización end-to-end diseñada para optimizar la recepción, validación y auditoría de facturas de proveedores. El sistema transforma documentos no estructurados (PDF/Imágenes) en datos estructurados mediante IA, permitiendo un monitoreo de KPIs en tiempo real.

## 🛠️ Arquitectura Técnica (API-First)
El proyecto integra diversas tecnologías líderes mediante el consumo de **APIs REST**:

*   **Orquestación:** [n8n](https://n8n.io/) (Self-hosted/Cloud) como motor de flujo de trabajo.
*   **Inteligencia Artificial:** [Azure AI Document Intelligence](https://azure.microsoft.com/es-es/products/ai-services/ai-document-intelligence) para el análisis semántico y extracción de entidades.
*   **Base de Datos:** PostgreSQL hospedado en [Neon](https://neon.tech/) para la persistencia de datos.
*   **Visualización:** [Power BI](https://powerbi.microsoft.com/) conectado vía **DirectQuery** para analítica en tiempo real.
*   **Notificaciones:** API de Gmail para el ciclo de feedback y alertas de auditoría.

## ⚙️ Funcionamiento del Pipeline
1.  **Ingesta:** Los documentos ingresan vía **Webhook** o integración con **Gmail API**.
2.  **Procesamiento de IA:** Se realiza una petición a la API de Azure para extraer campos clave (CUIT, Proveedor, Fecha, Importes).
3.  **Lógica de Auditoría:** Un nodo de **JavaScript** procesa el JSON, ejecuta controles aritméticos y asigna un KPI de "Tiempo Ahorrado" (5 min/doc).
4.  **Persistencia:** Los datos validados se insertan en una tabla **SQL** en Neon.
5.  **Monitoreo:** Power BI consume los datos para mostrar métricas de ahorro y alertas de integridad.

## 📊 KPIs Implementados
*   **Integridad de Datos:** Validación de CUITs y cálculos de IVA.
*   **Eficiencia Operativa:** Tracking automático de tiempo ahorrado (Minutos/Horas).
*   **Trazabilidad:** Auditoría completa del estado de procesamiento (Aprobado/Rechazado).

## 📈 Dashboard de Control de Integridad
<img width="906" height="510" alt="image" src="https://github.com/user-attachments/assets/96f6d1d5-2ca5-4448-b9d0-560bd8744a6a" />


## 🚀 Cómo ejecutarlo
1. Clonar el repositorio.
2. Configurar las variables de entorno para las **API Keys** de Azure y credenciales de PostgreSQL.
3. Importar el workflow `.json` en n8n.
