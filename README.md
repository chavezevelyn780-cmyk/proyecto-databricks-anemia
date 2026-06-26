# Sistema Inteligente de Monitoreo de Anemia y Gestión de Recursos en Hospitales

## Integrantes

- Chavez Calderon Evelyn
- Coronado Saavedra Noria
- Robles Lázaro Jesus
- Rodriguez Mancisidor Mauricio

---

# Descripción del Proyecto

La anemia infantil continúa siendo uno de los principales problemas de salud pública en el Perú, afectando el crecimiento y desarrollo de miles de niños. Asimismo, la adecuada distribución de los recursos hospitalarios constituye un factor clave para garantizar una atención médica eficiente y oportuna.

Este proyecto desarrolla una solución analítica utilizando **Databricks**, **Apache Spark** y la arquitectura **Medallion (Bronze, Silver y Gold)** para integrar, transformar y analizar información proveniente de registros de anemia y recursos hospitalarios.

Como resultado se obtiene un modelo analítico que permite monitorear la incidencia de anemia, identificar zonas críticas, evaluar la disponibilidad de recursos hospitalarios y generar indicadores estratégicos para apoyar la toma de decisiones en el sector salud.

---

# Objetivo General

Diseñar e implementar una solución analítica basada en Databricks que permita monitorear la incidencia de anemia infantil y evaluar la distribución de recursos hospitalarios mediante una arquitectura Medallion.

---

# Objetivos Específicos

- Integrar múltiples fuentes de datos relacionadas con anemia y hospitales.
- Aplicar procesos de limpieza y transformación de datos.
- Garantizar la calidad de la información mediante reglas de validación.
- Construir un modelo dimensional tipo estrella.
- Generar indicadores (KPIs) para el análisis del problema.
- Crear consultas analíticas para dashboards.
- Facilitar la toma de decisiones mediante visualizaciones en Power BI.

---

# Arquitectura de la Solución

El proyecto implementa la arquitectura **Medallion**, la cual organiza el procesamiento de datos en tres capas.

## Bronze

En esta capa se realiza la ingesta de los datos originales sin modificaciones.

Procesos realizados:

- Carga de archivos fuente.
- Conservación de la estructura original.
- Registro de fecha de carga.
- Registro del archivo origen.

---

## Silver

En esta capa se realiza el procesamiento y limpieza de la información.

Procesos realizados:

- Eliminación de registros duplicados.
- Tratamiento de valores nulos.
- Conversión de tipos de datos.
- Estandarización de nombres de columnas.
- Validación de reglas de negocio.
- Creación de columnas calculadas.

---

## Gold

En esta capa se construye el modelo analítico final.

Procesos realizados:

- Construcción de tablas dimensionales.
- Construcción de tabla de hechos.
- Generación de KPIs.
- Creación de vistas SQL.
- Preparación de información para Power BI.

---

# Arquitectura del Proyecto

```
                DATOS ORIGINALES
          (Anemia + Hospitales)

                    │
                    ▼

              BRONZE (Raw Data)

                    │

                    ▼

        SILVER (Limpieza y Calidad)

                    │

                    ▼

      GOLD (Modelo Analítico Estrella)

                    │

                    ▼

          SQL + Dashboards Power BI
```

---

# Herramientas Utilizadas

- Databricks
- Apache Spark
- PySpark
- Spark SQL
- Delta Lake
- Unity Catalog
- GitHub
- Microsoft Excel
- Power BI

---

# Modelo Analítico

## Tabla de Hechos

### FACT_ANEMIA

| Campo |
|--------|
| UBIGEO |
| AÑO |
| N_EVALUADOS |
| N_NIÑOS_ANEMIA |
| PORCENTAJE_ANEMIA |

---

## Dimensiones

### DIM_DISTRITO

- UBIGEO
- DISTRITO
- PROVINCIA
- ZONA

### DIM_HOSPITAL

- UBIGEO
- NOMBRE_HOSPITAL
- CAPACIDAD_PACIENTES
- NUM_MEDICOS
- NUM_ENFERMEROS
- NUM_AMBULANCIAS

### DIM_TIEMPO

- AÑO

---

# KPIs Implementados

- Porcentaje promedio de anemia.
- Número total de niños evaluados.
- Número de niños con anemia.
- Hospitales con menor capacidad.
- Distribución de médicos.
- Distribución de enfermeros.
- Recursos hospitalarios por provincia.
- Ranking de distritos con mayor incidencia de anemia.
- Evolución anual de la anemia.
- Recursos hospitalarios por zona.

---

# Preguntas Analíticas

El proyecto responde las siguientes preguntas de negocio:

1. ¿Qué distritos presentan la mayor incidencia de anemia?

2. ¿Cómo ha evolucionado la anemia entre 2023 y 2025?

3. ¿Qué provincias concentran el mayor porcentaje de anemia?

4. ¿Qué hospitales poseen menor capacidad de atención?

5. ¿Qué zonas requieren mayor asignación de recursos hospitalarios?

6. ¿Existe relación entre la incidencia de anemia y la disponibilidad de recursos hospitalarios?

---

# Estructura del Proyecto

```
Sistema-Inteligente-Monitoreo-Anemia-Hospitales
│
├── notebooks
│   ├── 01_ingesta_bronze.ipynb
│   ├── 02_transformacion_silver.ipynb
│   ├── 03_modelo_gold.ipynb
│   ├── 04_kpis_dashboard.ipynb
│
├── sql
│   ├── 01_creacion_tablas.sql
│   ├── 02_vistas_gold.sql
│   ├── 03_queries_dashboard.sql
│
├── docs
│   ├── arquitectura_medallion.png
│   ├── modelo_estrella.png
│   ├── diccionario_datos.md
│
├── dashboard
│   ├── Dashboard_Anemia.pbix
│   └── capturas_dashboard
│
├── conciliacion
│   └── conciliacion.xlsx
│
├── data_sample
│   ├── DAT_ANEMIA.xlsx
│   └── tabla_hospitales.xlsx
│
├── README.md
└── .gitignore
```

---

# Descripción de Carpetas

| Carpeta | Descripción |
|----------|-------------|
| notebooks | Contiene los notebooks de Databricks utilizados para cada etapa del procesamiento de datos. |
| sql | Scripts SQL para creación de tablas, vistas y consultas analíticas. |
| docs | Documentación del proyecto, arquitectura y diccionario de datos. |
| dashboard | Archivo Power BI y capturas del dashboard final. |
| conciliacion | Evidencias de validación y conciliación de resultados. |
| data_sample | Archivos de ejemplo utilizados durante el desarrollo del proyecto. |

---

# Flujo de Ejecución

El proyecto debe ejecutarse en el siguiente orden:

1. Ejecutar Notebook **01_ingesta_bronze**.
2. Ejecutar Notebook **02_transformacion_silver**.
3. Ejecutar Notebook **03_modelo_gold**.
4. Ejecutar Notebook **04_kpis_dashboard**.
5. Ejecutar los scripts SQL.
6. Actualizar el Dashboard en Power BI.
7. Validar resultados mediante el archivo de conciliación.

---

# Dashboard

El dashboard desarrollado en Power BI permite visualizar:

- Evolución anual de la anemia.
- Ranking de distritos con mayor incidencia.
- Ranking de provincias.
- Recursos hospitalarios disponibles.
- Capacidad hospitalaria.
- Indicadores generales (KPIs).
- Distribución geográfica de la anemia.

Las capturas del dashboard se encuentran en la carpeta:

```
dashboard/
```

---

# Resultados Obtenidos

La implementación de esta solución permitió:

- Integrar múltiples fuentes de información mediante Databricks.
- Mejorar la calidad de los datos aplicando procesos ETL.
- Construir un modelo analítico escalable utilizando arquitectura Medallion.
- Generar indicadores estratégicos para la gestión hospitalaria.
- Identificar distritos con mayor incidencia de anemia.
- Evaluar la distribución de recursos hospitalarios.
- Facilitar el análisis mediante dashboards interactivos en Power BI.

---

# Tecnologías

| Tecnología | Uso |
|------------|-----|
| Databricks | Plataforma principal de procesamiento |
| Apache Spark | Procesamiento distribuido |
| PySpark | Transformaciones ETL |
| SQL | Consultas analíticas |
| Delta Lake | Almacenamiento de tablas |
| GitHub | Control de versiones |
| Excel | Validación y conciliación |
| Power BI | Visualización de resultados |

---

# Conclusión

La arquitectura Medallion implementada permitió organizar el procesamiento de datos de forma eficiente, garantizando la calidad de la información y facilitando la construcción de indicadores estratégicos. El modelo desarrollado constituye una herramienta de apoyo para la toma de decisiones relacionadas con el monitoreo de la anemia infantil y la gestión de recursos hospitalarios, proporcionando información confiable para el análisis y la planificación en el sector salud.
