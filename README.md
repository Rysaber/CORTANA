![n8n](https://img.shields.io/badge/Powered_by-n8n-2088FF?logo=n8n&logoColor=white)
![OpenAI](https://img.shields.io/badge/LLM-GPT--4-blueviolet?logo=openai)
![Google Sheets](https://img.shields.io/badge/Data-Google_Sheets-34A853?logo=google-sheets&logoColor=white)
![Calendar](https://img.shields.io/badge/Calendar-Google_Calendar-blue?logo=google-calendar&logoColor=white)
![Telegram](https://img.shields.io/badge/Bot-Telegram-229ED9?logo=telegram)

# 🤖 Cortana Virtual Assistant con MCP Server (n8n)

Este proyecto conecta un **asistente virtual inteligente llamado Cortana** con un servidor MCP en n8n para permitir la automatización de tareas personales a través de comandos en lenguaje natural o voz, usando **Telegram como canal principal**.

---

## 🧠 ¿Qué es Cortana?

Cortana es una asistente virtual construida sobre `n8n`, `LangChain`, `OpenAI` y `Google Services`. Es capaz de:

- Procesar mensajes de texto o voz desde Telegram.
- Interpretar intenciones del usuario usando modelos LLM (GPT-4).
- Ejecutar acciones automatizadas mediante herramientas (tools) conectadas al servidor MCP.

---

## 🌐 ¿Qué es MCP Server?

El **MCP Server** actúa como backend para ejecutar tareas como:

- **Gestionar contraseñas** (consultar o guardar) desde una hoja de Google Sheets.
- **Crear, consultar, eliminar o reprogramar citas** en Google Calendar.
- **Manejar notas personales** como recordatorios informales.

Está compuesto por herramientas personalizadas que el agente Cortana invoca dinámicamente usando el `MCP Client Tool`.

---

## 🧩 Componentes del Proyecto

### 1. `ASISTENTE_CORTANA` (Flujo n8n)
- **Entrada:** mensajes de texto o audio por Telegram.
- **Procesamiento NLP:** OpenAI + LLM Chain + Memory Postgres.
- **Tareas soportadas:**
  - Agendar, reprogramar, consultar o eliminar citas.
  - Guardar, consultar o eliminar notas informales.
  - Consultar contraseñas personales por app o todas.
- **Respuesta adaptativa:** en texto o voz según la entrada del usuario.

### 2. `MCP_SERVER` (Flujo n8n)
- **Entrada:** peticiones JSON desde el `MCP Client Tool`.
- **Herramientas disponibles:**
  - `consultar_password`: busca contraseñas en Google Sheets.
  - `guardar_password`: (pendiente en este flujo).
  - `agendar_cita`, `reprogramar_cita`, `eliminar_cita`, `consultar_citas`: interactúan con Google Calendar.
  - `guardar_nota`, `consultar_notas`, `eliminar_nota`: gestionan recordatorios informales en Sheets.

---

## 📦 Requisitos

- Cuenta en [n8n](https://n8n.io/)
- API Key de [OpenAI](https://platform.openai.com/)
- Cuenta de Google con acceso a:
  - Google Calendar
  - Google Sheets (documento configurado con pestañas para contraseñas y recordatorios)
- Bot de Telegram configurado y enlazado con n8n
- Base de datos Postgres para memoria conversacional (opcional, pero recomendado)

---

## ⚙️ Instalación

1. Clona este repositorio:
```bash
git clone https://github.com/Rysaber/CORTANA.git

