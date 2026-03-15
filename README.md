# ANÁLISIS DE DATOS DEMOGRÁFICOS MUNDIALES MEDIANTE TÉCNICAS ETL, EDA Y MACHINE LEARNING UTILIZANDO LA API REST COUNTRIES

## Descripción
Este proyecto desarrolla un flujo completo de analítica de datos sobre países del mundo usando la API REST Countries.

El trabajo está organizado en tres etapas principales:
1. ETL: extracción, transformación y carga de datos demográficos.
2. EDA: análisis exploratorio con generación de gráficas.
3. Machine Learning: clasificación de países por región usando Árbol de Decisión.

## Objetivo general
Construir un pipeline reproducible que permita:
- Obtener datos crudos de países desde una API pública.
- Estandarizar las variables relevantes para análisis.
- Explorar visualmente patrones demográficos globales.
- Entrenar un modelo de clasificación para predecir la región de un país a partir de sus variables demográficas.

## Estructura del proyecto
```text
PARCIAL/
├── main.py
├── ETL/
│   ├── fase1_extraccion.py
│   ├── fase2_transformacion.py
│   └── fase3_carga.py
├── JSON/
│   └── paises_transformados.json
├── EDA/
│   └── graficas.py
└── MACHINE_LEARNING/
    ├── modelo_arbol_decision.py
    ├── reporte_precision.txt
    └── grafico_arbol.png
```

## Tecnologías y librerías
- Python 3.10+
- requests
- pandas
- numpy
- matplotlib
- scikit-learn

Instalación rápida:
```bash
pip install requests pandas numpy matplotlib scikit-learn
```

## Flujo ETL
### Fase 1: Extracción
Archivo: `ETL/fase1_extraccion.py`
- Consume el endpoint: `https://restcountries.com/v3.1/all`.
- Incluye manejo de errores HTTP y fallback con campos mínimos cuando aplica.

### Fase 2: Transformación
Archivo: `ETL/fase2_transformacion.py`
- Selecciona y simplifica variables clave por país:
  - nombre
  - capital
  - region
  - poblacion
  - area

### Fase 3: Carga
Archivo: `ETL/fase3_carga.py`
- Guarda los datos transformados en formato JSON local.

### Ejecución ETL
```bash
python main.py
```
Salida esperada:
- `JSON/paises_transformados.json`

## Análisis Exploratorio de Datos (EDA)
Archivo: `EDA/graficas.py`

Genera 8 visualizaciones:
1. Cantidad de países por región.
2. Población total por región.
3. Área total por región.
4. Dispersión área vs población (escala log-log).
5. Top 10 países más poblados.
6. Mapa de calor de correlación (población, área, densidad).
7. Mapa de calor de métricas promedio por región.
8. Gráfico de pastel de países por región.

### Ejecución EDA
```bash
python EDA/graficas.py
```
Salidas esperadas:
- `EDA/01_cantidad_paises_por_region.png`
- `EDA/02_poblacion_total_por_region.png`
- `EDA/03_area_total_por_region.png`
- `EDA/04_dispersion_area_vs_poblacion.png`
- `EDA/05_top10_paises_mas_poblados.png`
- `EDA/06_mapa_calor_correlacion.png`
- `EDA/07_mapa_calor_metricas_por_region.png`
- `EDA/08_pastel_paises_por_region.png`

## Machine Learning
Archivo: `MACHINE_LEARNING/modelo_arbol_decision.py`

### Problema modelado
Clasificación multiclase para predecir la región (`region`) a partir de:
- `poblacion`
- `area`

### Metodología
- Limpieza de nulos.
- Codificación de etiquetas con `LabelEncoder`.
- División entrenamiento/prueba con `train_test_split` (80/20, estratificado).
- Entrenamiento con `DecisionTreeClassifier` (criterio Gini).
- Evaluación con `classification_report`.

### Ejecución ML
```bash
python MACHINE_LEARNING/modelo_arbol_decision.py
```

Salidas esperadas:
- Reporte de clasificación en `.txt`.
- Visualización del árbol en `.png`.

## Resultados actuales (resumen)
Según el reporte incluido:
- Accuracy global aproximada: 0.30
- Macro F1 aproximado: 0.27
- Clases con mejor desempeño relativo: Asia y Oceania

## Orden recomendado de ejecución
1. Ejecutar ETL:
```bash
python main.py
```
2. Ejecutar EDA:
```bash
python EDA/graficas.py
```
3. Ejecutar Machine Learning:
```bash
python MACHINE_LEARNING/modelo_arbol_decision.py
```

## Autor
Tomas Uribe Sanchez 
Estudianten de Ingenieria de Sistemas
Proyecto académico de Analítica de Datos.
