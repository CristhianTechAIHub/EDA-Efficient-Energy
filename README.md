# Análisis Exploratorio de Datos: Eficiencia Energética de Edificios

## Descripción del Proyecto

Este proyecto presenta un Análisis Exploratorio de Datos (EDA) del dataset "Energy Efficiency" con el objetivo de identificar las características arquitectónicas que más influyen en las cargas de calefacción (Heating Load) y refrigeración (Cooling Load) de edificios residenciales.

Como ingeniero mecatrónico, este análisis busca conectar los patrones estadísticos de los datos con sus fundamentos físicos y de ingeniería, sentando las bases para un futuro modelo de Machine Learning.

## Dataset

- **Nombre:** Energy Efficiency Dataset
- **Fuente:** Kaggle
- **Enlace:** [https://www.kaggle.com/datasets/elikplim/eergy-efficiency-dataset](https://www.kaggle.com/datasets/elikplim/eergy-efficiency-dataset)

El dataset contiene 768 muestras de edificios simulados con 8 características (X1-X8) y 2 variables objetivo (y1-y2).

## Metodología

El análisis se estructuró siguiendo los siguientes pasos:

1.  **Carga y Limpieza de Datos:** Importación del dataset y asignación de nombres descriptivos a las columnas para mejorar la legibilidad del análisis.
2.  **Análisis Univariado:** Visualización de la distribución de cada variable mediante histogramas para identificar patrones como bimodalidad, sesgos y la falta de una distribución normal en los datos.
3.  **Análisis de Correlación:** Debido a la no normalidad de los datos, se seleccionó la matriz de **correlación de Spearman** para evaluar las relaciones monótonas entre las variables. La matriz fue visualizada con un mapa de calor para una fácil interpretación.

## Hallazgos Clave

El análisis reveló varias ideas importantes sobre la relación entre el diseño de un edificio y su consumo energético:

* **Variables más influyentes:** La `Altura total` y el `Área de techo` son los predictores más significativos para las cargas de energía, con correlaciones fuertes (positiva de 0.86 y negativa de -0.80, respectivamente). Esto se alinea con los principios de la termodinámica, donde el área de transferencia de calor es un factor clave.
* **Multicolinealidad Crítica:** Se detectó una correlación negativa perfecta (-1.00) entre la `Compacidad relativa` y el `Área de superficie`, indicando que son variables redundantes. De manera similar, la `Carga de calefacción` y la `Carga de refrigeración` tienen una correlación de 0.97, lo que las hace casi intercambiables.
* **Variables de Bajo Impacto:** La `Orientación` del edificio no muestra una correlación significativa con ninguna de las variables objetivo, sugiriendo un bajo poder predictivo en este dataset.
* **Distribuciones No Normales:** Ninguna de las variables sigue una distribución normal. Características como la `Altura total` presentan una clara bimodalidad, probablemente representando edificios de 1 y 2 pisos.

## Recomendaciones y Próximos Pasos

Basado en este EDA, los siguientes pasos serían:

1.  Para el desarrollo de un modelo predictivo, se recomienda **excluir una de las variables de cada par con alta multicolinealidad** (ej. quedarse con `Compacidad relativa` y descartar `Área de superficie`).
2.  Las variables `Altura total` y `Área de techo` deben ser consideradas como características primarias en cualquier modelo de predicción.
3.  Realizar **ingeniería de características** (Feature Engineering) para crear nuevas variables que puedan mejorar la precisión del modelo, como convertir la `Altura total` en una variable categórica ('Número de pisos').

## Cómo Ejecutar este Notebook

### Requisitos

Para ejecutar el notebook `EDA_v2.ipynb`, se necesita una instalación de **Conda** y las librerías especificadas en el archivo `environment.yml`.

### Instalación del Entorno de Conda

1.  **Clona este repositorio** en tu máquina local.
2.  **Abre una terminal** (o Anaconda Prompt) y navega hasta la carpeta raíz del proyecto.
3.  **Crea el entorno de Conda** a partir del archivo `environment.yml`. Esto instalará todas las dependencias necesarias.
    ```bash
    conda env create -f environment.yml
    ```
4.  **Activa el nuevo entorno** llamado `EDA`.
    ```bash
    conda activate EDA
    ```
5.  Una vez activado el entorno, puedes **abrir Jupyter Notebook o Jupyter Lab** para ejecutar el notebook.
    ```bash
    jupyter notebook
    ```