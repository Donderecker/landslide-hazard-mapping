# Landslide Susceptibility Assessment using Weighted Overlay

Este proyecto presenta un flujo de trabajo para evaluar la susceptibilidad a deslizamientos mediante un análisis multicriterio (*Weighted Overlay*), utilizando Python y QGIS. El modelo integra variables ambientales previamente reclasificadas para generar un mapa de susceptibilidad que identifica sectores con mayor probabilidad de ocurrencia de procesos de remoción en masa.

---

# Overview | Descripción general

El análisis multicriterio (*Multi-Criteria Decision Analysis*, MCDA) es una metodología ampliamente utilizada en Sistemas de Información Geográfica para integrar múltiples variables espaciales mediante criterios y ponderaciones previamente definidos.

En este proyecto se implementa una combinación lineal ponderada (*Weighted Overlay*), donde variables como pendiente, distancia a fallas geológicas, ambiente geológico y proximidad a la red de drenaje son reclasificadas e integradas para obtener un índice final de susceptibilidad a deslizamientos.


**Importante:** Este código está diseñado específicamente para análisis 
de remociones en masa en contextos de fallas geológicas activas.

⚠️ NO usar este modelo en áreas sin fallas o estructuras geológicas 
similares sin validación previa.

---

# Study Area | Área de estudio

(Descripción del área utilizada durante el ejercicio).

<p align="center">
<img src="images/study-area.png" width="850">
</p>

---

# Workflow | Flujo de trabajo

La siguiente figura resume la metodología desarrollada durante el proyecto.

<p align="center">
<img src="images/workflow.png" width="900">
</p>

---

# Input Data | Datos de entrada

Para reproducir el análisis se requieren las siguientes capas:

- Modelo Digital de Elevación (DEM)
- Fallas geológicas
- Ambiente geológico
- Red de drenaje
- Límite del área de estudio

---

# Methodology | Metodología

## 1. Geological Fault Distance | Distancia a fallas geológicas

Las fallas geológicas fueron rasterizadas y posteriormente se calculó la distancia euclidiana desde cada píxel hasta la falla más cercana.

(imagen)

---

## 2. Geological Environment | Ambiente geológico

Las unidades geológicas fueron reclasificadas según su susceptibilidad relativa a procesos de remoción en masa.

(imagen)

---

## 3. Slope | Pendiente

La pendiente fue calculada a partir del Modelo Digital de Elevación y posteriormente reclasificada en categorías de susceptibilidad.

(imagen)

---

## 4. Drainage Network | Red de drenaje

Se calculó la distancia a la red hidrográfica y posteriormente se reclasificó para integrarla al análisis multicriterio.

(imagen)

---

## 5. Weighted Overlay | Suma ponderada

Las variables reclasificadas fueron combinadas mediante una suma ponderada para obtener el índice final de susceptibilidad.

(imagen)

---

# Results | Resultados

## Landslide Susceptibility Map

(imagen final)

El modelo permitió identificar los sectores con mayor susceptibilidad a deslizamientos dentro del área de estudio.

Durante el ejercicio se obtuvo una superficie de **193.79 km²** con un índice de susceptibilidad igual o superior a **2.5**.

Posteriormente, mediante un muestreo raster sobre propiedades, se identificó que **77 propiedades** se encuentran localizadas dentro de zonas con susceptibilidad igual o superior al umbral establecido.

---

# Data Availability | Disponibilidad de los datos

Los datos originales no se incluyen en este repositorio debido al tamaño de los archivos.

Los insumos necesarios corresponden a:

- Modelo Digital de Elevación.
- Fallas geológicas.
- Ambiente geológico.
- Red hidrográfica.
- Raster de susceptibilidad generado.

---

# Software | Software utilizado

- Python
- Jupyter Notebook
- QGIS
- GeoPandas
- Rasterio
- GDAL
- NumPy
- Matplotlib

---

# Resources | Recursos utilizados

El flujo completo de procesamiento se encuentra documentado en:

- `notebooks/weighted_overlay.ipynb`

---

# Acknowledgements | Agradecimientos

_Este proyecto fue desarrollado originalmente como parte del curso **Aplicaciones de los Sistemas de Información Geográfica (SIG) y Ordenamiento Territorial con SIG y TICs** de la carrera de **Geografía** de la **Universidad Austral de Chile (UACh)**._

La actividad original fue adaptada para este repositorio con el propósito de documentar un flujo de trabajo reproducible para la evaluación de susceptibilidad a deslizamientos mediante análisis multicriterio (*Weighted Overlay*), utilizando Python y QGIS.


