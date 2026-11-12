# Análisis de retrasos en vuelos de Nueva York

[**Abrir la aplicación en Streamlit**](https://vuelos-app-guille.streamlit.app/)

Aplicación interactiva para explorar los retrasos de llegada de **325.802 vuelos completados** que salieron de Nueva York en 2013 desde **JFK, LaGuardia (LGA) y Newark (EWR)**. El proyecto analiza cómo se relacionan la hora programada, el clima y la antigüedad del avión con la puntualidad. Se desarrolló como parte de la semana 15 de Big Data.

## Qué puedes explorar

| Vista | Qué muestra |
| --- | --- |
| **Indicadores** | Número de vuelos, porcentaje de llegadas tardías, retraso promedio y correlación entre la hora programada y el retraso de llegada. |
| **Matriz de correlación** | Relaciones entre variables numéricas mediante Pearson o Spearman. |
| **Hora y clima** | Porcentaje de llegadas tardías por franja horaria y con o sin lluvia. |
| **Explorar una variable** | Tasa de llegadas tardías por intervalos de una variable, como la edad del avión o la visibilidad. |
| **Datos filtrados** | Vista previa de hasta 500 filas y descarga en CSV de todos los vuelos que coinciden con los filtros. |

La barra lateral permite combinar filtros por **aerolínea, aeropuerto de salida y rango de meses**. Una llegada se considera tardía cuando ocurre **15 minutos o más** después de la hora prevista.

## Resultados principales

| Indicador | Resultado en el conjunto analizado |
| --- | ---: |
| Llegadas tardías | 24,4 % |
| Retraso promedio de llegada | 6,9 minutos |
| Llegadas tardías en la mañana / en la noche | 15,2 % / 35,8 % |
| Llegadas tardías sin lluvia / con lluvia | 22,8 % / 48,6 % |
| Correlación de Pearson entre retraso de salida y de llegada | 0,92 |
| Correlación de Pearson entre edad del avión y retraso de llegada | −0,02 |

El retraso de salida presenta la asociación más fuerte con el retraso de llegada y puede servir como alerta una vez que se conoce la hora real de salida. La tasa de llegadas tardías aumenta en las franjas más avanzadas del día y es mayor entre los vuelos que salieron con lluvia. La edad del avión muestra una asociación lineal prácticamente nula entre los vuelos con ese dato disponible.

Estas cifras describen asociaciones en los vuelos completados de tres aeropuertos durante 2013. Una evaluación de cambios operativos tendría que comparar vuelos similares por ruta, aerolínea, temporada y condiciones meteorológicas.

## Datos y metodología

El archivo comprimido reúne registros de vuelos, clima, aviones, aerolíneas y aeropuertos. Durante la preparación se retiraron los vuelos sin hora de salida o sin dato de retraso de llegada, se integró el clima por aeropuerto de origen y hora programada, y se convirtieron las medidas meteorológicas y de distancia al sistema métrico. El conjunto final contiene **23 columnas**.

El análisis exploratorio se hizo con **pandas y Plotly**. La app usa **Streamlit** para la interfaz y **SciPy** para el cálculo de Spearman a través de pandas.

## Ejecutar en local

Clona el repositorio, instala las dependencias y ejecuta la app desde la raíz del proyecto.

```bash
git clone https://github.com/gpazop/vuelos-app-equipo.git
cd vuelos-app-equipo
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Abre [localhost:8501](http://localhost:8501) en el navegador. Mantén el archivo `vuelos_limpio.csv.gz` junto a `app.py`. La aplicación lee el archivo comprimido directamente.

## Archivos del proyecto

| Archivo | Contenido |
| --- | --- |
| [app.py](app.py) | Código de la interfaz, los filtros, los indicadores y los gráficos. |
| [requirements.txt](requirements.txt) | Dependencias de Python. |
| [vuelos_limpio.csv.gz](vuelos_limpio.csv.gz) | Dataset limpio que utiliza la aplicación. |

**Autor:** Guillermo Arturo Pazo Purizaca.
