# Landslide Susceptibility Assessment using Weighted Overlay

Este proyecto presenta un flujo de trabajo para evaluar la susceptibilidad a movimientos en masa mediante un análisis multicriterio (*Weighted Overlay*), utilizando **Python**, **QGIS** y **Jupyter Notebook**. El modelo integra variables ambientales previamente reclasificadas para generar un mapa de susceptibilidad que identifica sectores con mayor probabilidad de ocurrencia de deslizamientos.

---

# Requirements | Requisitos

<p align="center">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="90">
  &nbsp;&nbsp;&nbsp;
  <img src="https://upload.wikimedia.org/wikipedia/commons/7/77/Qgis-icon-3.0.png" width="90">
  &nbsp;&nbsp;&nbsp;
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/jupyter/jupyter-original.svg" width="90">
</p>

Para reproducir este proyecto se requiere trabajar de forma complementaria entre **QGIS** y **Jupyter Notebook**.

* **QGIS** se utiliza para generar y procesar las capas raster mediante las herramientas de **GDAL**, **GRASS GIS** y **Processing Toolbox**.
* **Jupyter Notebook** se utiliza para integrar las variables, aplicar la suma ponderada, visualizar los resultados y generar el mapa final de susceptibilidad.

> **⚠️ Importante**
>
> Antes de ejecutar el notebook, modifique las rutas de los archivos para que coincidan con la ubicación de los datos en su propio entorno de trabajo.

---

# Overview | Descripción general

El análisis multicriterio (*Multi-Criteria Decision Analysis*, MCDA) es una metodología ampliamente utilizada en Sistemas de Información Geográfica para integrar múltiples variables espaciales mediante criterios y ponderaciones previamente definidos.

En este proyecto se implementa una combinación lineal ponderada (*Weighted Overlay*), donde variables como la pendiente, la distancia a fallas geológicas y el ambiente geológico son reclasificadas e integradas para obtener un índice de susceptibilidad a movimientos en masa.

> **⚠️ Importante**
>
> Este modelo fue desarrollado con fines académicos y considera variables específicas utilizadas durante el ejercicio. Su aplicación en otras áreas requiere adaptar los criterios de clasificación, las ponderaciones y validar previamente los resultados obtenidos.

---

# Workflow | Flujo de trabajo

La siguiente figura resume la metodología implementada durante el proyecto.

<p align="center">
<img src="images/weighted_overlay_variables.png" width="900">
</p>

---

# Input Data | Datos de entrada

Para reproducir el análisis se requieren los siguientes insumos:

* Modelo Digital de Elevación (DEM)
* Capa vectorial de fallas geológicas
* Capa vectorial de ambiente geológico

Los datos originales no se incluyen en este repositorio debido al tamaño de los archivos.

---

# Methodology | Metodología

## 1. Geological Fault Distance | Distancia a fallas geológicas

La capa de fallas geológicas fue rasterizada y posteriormente se calculó la distancia euclidiana desde cada píxel hasta la falla más cercana. Finalmente, el raster fue reclasificado en cuatro categorías de susceptibilidad.

### Herramientas utilizadas en QGIS

```text
gdal:rasterize
gdal:proximity
grass7:r.reclass
```

---

## 2. Geological Environment | Ambiente geológico

Las unidades geológicas fueron reclasificadas asignando un valor de susceptibilidad a cada ambiente geológico. Posteriormente, la capa vectorial fue convertida a formato raster para integrarla al análisis multicriterio.

### Herramientas utilizadas en QGIS

```text
GeoPandas
gdal:rasterize
```

---

## 3. Slope | Pendiente

La pendiente fue calculada a partir del Modelo Digital de Elevación y posteriormente reclasificada en cuatro niveles de susceptibilidad.

### Herramientas utilizadas en QGIS

```text
native:slope
grass7:r.reclass
```

---

## 4. Weighted Overlay | Suma ponderada

Las variables raster reclasificadas fueron integradas mediante una combinación lineal ponderada. En este ejercicio se asignó una mayor ponderación a la pendiente respecto de las demás variables, obteniendo un índice final de susceptibilidad a movimientos en masa.

<p align="center">
<img src="images/Mass_movement_hazard.png" width="900">
</p>

---

# Results | Resultados

El mapa final representa la distribución espacial de la susceptibilidad a movimientos en masa obtenida mediante el análisis multicriterio.

<p align="center">
<img src="images/hazard_mapping.png" width="900">
</p>

Como resultado del ejercicio:

* La superficie con un índice de susceptibilidad **mayor o igual a 2.5** corresponde a **193.79 km²**.
* El muestreo del raster sobre el conjunto de propiedades identificó **28 propiedades** localizadas en zonas con susceptibilidad **mayor o igual a 2.5**.

---

# Data Availability | Disponibilidad de los datos

Los datos originales no se incluyen en este repositorio debido al tamaño de los archivos.

Para reproducir el análisis se requieren:

* Modelo Digital de Elevación (DEM)
* Fallas geológicas
* Ambiente geológico
* Raster de susceptibilidad generado

---

# Software | Software utilizado

* Python
* Jupyter Notebook
* QGIS
* GDAL
* GRASS GIS
* GeoPandas
* Rasterio
* NumPy
* Matplotlib

---

# Resources | Recursos utilizados

El flujo completo del procesamiento se encuentra documentado en:

* `notebooks/weighted_overlay_colab.ipynb`

Durante el desarrollo del proyecto se utilizaron los siguientes directorios del repositorio:

* `data/raster/` — Archivos raster de entrada (DEM y demás capas raster).
* `data/vector/` — Capas vectoriales originales (GeoPackage).
* `data/processed/` — Capas raster generadas durante el procesamiento.
* `images/` — Figuras utilizadas en esta documentación.
* `outputs/` — Productos finales generados por el análisis.

> **Nota:** Antes de ejecutar el notebook, actualice las rutas de los archivos para que apunten a los directorios correspondientes dentro de su propio entorno de trabajo.

---

# Acknowledgements | Agradecimientos

*Este proyecto fue desarrollado originalmente como parte del curso **Aplicaciones de los Sistemas de Información Geográfica (SIG) y Ordenamiento Territorial con SIG y TICs** de la carrera de **Geografía** de la **Universidad Austral de Chile (UACh)**.*

La actividad original fue adaptada para este repositorio con el propósito de documentar un flujo de trabajo reproducible para la evaluación de susceptibilidad a movimientos en masa mediante un análisis multicriterio (*Weighted Overlay*), utilizando **Python**, **QGIS** y **Jupyter Notebook**.
