# 🦜 Asistente de Análisis de Datos con IA

Este proyecto es una aplicación web interactiva construida con **Streamlit** y **Langchain**, diseñada para actuar como un asistente inteligente de análisis de datos. Permite a los usuarios subir un archivo CSV y explorar sus datos utilizando lenguaje natural, potenciado por modelos de lenguaje grandes (LLMs) a través de la API de **Groq** (específicamente utilizando el modelo `llama-3.1-8b-instant`).

## 🚀 Características Principales

La aplicación ofrece un conjunto de herramientas especializadas para el análisis de datos automatizado:

1. 📄 **Reporte de Información General:**
   Genera automáticamente un resumen sobre la estructura del dataset, incluyendo dimensiones, tipos de datos, recuento de nulos/duplicados y sugerencias de tratamiento de datos.

2. 📄 **Reporte de Estadísticas Descriptivas:**
   Crea un análisis estadístico profundo, calculando métricas clave (media, mediana, desviación estándar), identificando valores atípicos (outliers) y recomendando próximos pasos analíticos.

3. 🔎 **Preguntas en Lenguaje Natural (Q&A de Datos):**
   Gracias a un agente React de Langchain (`PythonAstREPLTool`), los usuarios pueden hacer preguntas específicas sobre sus datos (ej. *"¿Cuál es el promedio de tiempo de entrega?"*) y el agente escribirá y ejecutará código Python en tiempo real para obtener la respuesta.

4. 📊 **Generación Automática de Gráficos:**
   Permite visualizar datos simplemente pidiéndolo (ej. *"Genera un gráfico del promedio de ventas por categoría"*). El sistema interpreta la solicitud, genera código usando `matplotlib` y `seaborn`, y renderiza el gráfico en la interfaz.

## 🛠️ Tecnologías Utilizadas

* **[Streamlit](https://streamlit.io/):** Interfaz gráfica de usuario ágil e interactiva.
* **[Langchain](https://python.langchain.com/):** Framework para orquestar los agentes, herramientas (Tools) y prompts.
* **[Groq](https://groq.com/):** Proveedor del modelo de lenguaje LLaMA para procesamiento ultrarrápido.
* **[Pandas](https://pandas.pydata.org/):** Manipulación y análisis de DataFrames subyacentes.
* **[Matplotlib & Seaborn]:** Creación de visualizaciones dinámicas.

## ⚙️ Requisitos previos e Instalación

1. Clona este repositorio o descarga el código.
2. Crea un entorno virtual (recomendado):
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
4. Configura tu variable de entorno para Groq:
   * Crea un archivo `.env` en la raíz del proyecto.
   * Agrega tu clave de API:
     ```env
     GROQ_API_KEY=tu_api_key_aqui
     ```

## 🏃 Cómo ejecutar la aplicación

Abre tu terminal con el entorno virtual activado y ejecuta el siguiente comando:

```bash
streamlit run app.py
```

Esto abrirá una pestaña en tu navegador web por defecto (típicamente en `http://localhost:8501`) donde podrás cargar tu archivo `.csv` y comenzar a analizar.

## 📂 Estructura de Archivos

* `app.py`: Archivo principal que contiene la interfaz gráfica de Streamlit y la orquestación principal del agente Langchain.
* `herramientas.py`: Contiene la definición de las diferentes herramientas (`@tool`) que Langchain utiliza para interactuar con los datos (generador de reportes, analista de gráficos y ejecutor de Python).
* `requirements.txt`: Lista de dependencias del proyecto.
* `.env`: Archivo de variables de entorno (no incluido en el repositorio por seguridad) para llaves de API.
