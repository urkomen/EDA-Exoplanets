# Exoplanetas, Habitabilidad y la Paradoja de Fermi - EDA

<div align="center">
<img src="./src/img/p_fermi.jpeg" width="800" height="400">
</div>

## Descripción

Este proyecto realiza un **Análisis Exploratorio de Datos (EDA)** sobre exoplanetas, evaluando su habitabilidad y planteando la Paradoja de Fermi. El análisis combina datos astronómicos reales con ciencia y filosofía de forma accesible y atractiva.

La clave de este análisis es centrarse en los factores que afectan a la probabilidad de la existencia de civilizaciones usando datos astronómicos, sin especular sobre alienígenas. Se estudian parámetros como tamaños, temperaturas, distancias, tipos de estrella y zonas habitables para responder a la famosa pregunta: **"¿Hay vida ahí fuera?"**

---

## Hipótesis de Trabajo

El proyecto se estructura alrededor de 6 hipótesis principales:

>**H1**: Los exoplanetas con temperaturas compatibles con agua líquida tienen radios similares a los de la Tierra (¿y las masas?).
>**H2**: Los métodos actuales detectan preferentemente planetas grandes y calientes, no los más habitables.
>**H3**: Las estrellas más estables (actividad baja) tienen más planetas potencialmente habitables.
>**H4**: El porcentaje de planetas *Tipo Tierra* es extremadamente bajo dentro del catálogo conocido.
>**H5**: La mayoría de las estrellas cercanas no cumplen simultáneamente condiciones para la vida inteligente (edad, estabilidad, metalicidad, zona habitable...).
>**H6**: La distancia media entre planetas potencialmente habitables es tan grande que la comunicación entre sí o viajes interestelares es muy improbable.

---

## Estructura del Proyecto

```
src/
├── data/                          # Datos del proyecto
│   ├── PSCompPars_2026.03.31_03.43.51.csv   # Dataset original NASA
│   ├── pscomppars_API.csv                    # Dataset obtenido vía API
│   ├── dataclean_pl.csv                      # Datos limpios de planetas
│   ├── dataclean_st.csv                      # Datos limpios de estrellas
│   ├── dataclean_sy.csv                      # Datos limpios de sistemas
│   └── columns.txt                           # Documentación de columnas
│
├── notebooks/                     # Notebooks de análisis
│   ├── dataset.ipynb              # Obtención y exploración inicial del dataset
│   ├── data_clean.ipynb           # Limpieza y preparación de datos
│   └── analisis.ipynb             # Análisis exploratorio completo
│
├── img/                           # Imágenes y recursos visuales
│   └── p_fermi.jpeg               # Imagen principal (Paradoja de Fermi)
│
└── EDA_definicion.ipynb           # Notebook principal con definición del proyecto
```

---

## Fuente de Datos

Los datos provienen de la **[NASA Exoplanet Archive](http://exoplanetarchive.ipac.caltech.edu)**, específicamente de la tabla **Planetary Systems Composite Data**. Este dataset contiene información compuesta de múltiples fuentes sobre sistemas planetarios confirmados.

- **Fecha de obtención**: Marzo 2026
- **Formato original**: CSV
- **Total de columnas originales**: ~300+ variables
- **Columnas seleccionadas para el análisis**: ~25 variables clave

---

## Variables Principales

### Planetas
| Variable | Descripción | Unidad |
|----------|-------------|--------|
| `pl_name` | Nombre del planeta | - |
| `pl_rade` | Radio del planeta | Radios terrestres (R⊕) |
| `pl_bmasse` | Masa del planeta | Masas terrestres (M⊕) |
| `pl_eqt` | Temperatura de equilibrio | Kelvin (K) |
| `pl_orbper` | Período orbital | Días |
| `pl_orbsmax` | Semieje mayor | UA |
| `pl_insol` | Insolación recibida | Flujo terrestre |

### Estrellas
| Variable | Descripción | Unidad |
|----------|-------------|--------|
| `hostname` | Nombre de la estrella | - |
| `st_teff` | Temperatura efectiva | Kelvin (K) |
| `st_rad` | Radio estelar | Radios solares |
| `st_mass` | Masa estelar | Masas solares |
| `st_met` | Metalicidad | dex |
| `st_spectype` | Tipo espectral | Clasificación (O, B, A, F, G, K, M) |
| `st_age` | Edad estimada | Gyr |
| `st_rotp` | Período de rotación | Días |

### Sistemas
| Variable | Descripción | Unidad |
|----------|-------------|--------|
| `sy_dist` | Distancia | Parsecs (pc) |
| `sy_pnum` | Número de planetas | - |
| `discoverymethod` | Método de detección | - |
| `disc_year` | Año de descubrimiento | - |

---

## Metodología

### 1. Obtención de Datos (`dataset.ipynb`)
- Descarga desde la NASA Exoplanet Archive
- Exploración inicial del dataset
- Identificación de variables relevantes

### 2. Limpieza de Datos (`data_clean.ipynb`)
- Selección de columnas imprescindibles
- Tratamiento de valores nulos
- Filtrado y transformación de datos
- Generación de 3 datasets limpios:
  - **Planetas** (`dataclean_pl.csv`)
  - **Estrellas** (`dataclean_st.csv`)
  - **Sistemas** (`dataclean_sy.csv`)

### 3. Análisis Exploratorio (`analisis.ipynb`)

#### Análisis Univariante
- **Planetas**: Distribución de radios, masas, temperaturas, períodos orbitales
- **Estrellas**: Tipos espectrales, metalicidad, edades
- **Sistemas**: Métodos de detección, distribución temporal de descubrimientos

#### Análisis Bivariante
- Radio vs Masa del Planeta
- Metalicidad vs Masa del Planeta
- Edad de la Estrella vs Número de Planetas

#### Validación de Hipótesis
Cada una de las 6 hipótesis se analiza individualmente con visualizaciones y estadísticas descriptivas.

---

## Tecnologías Utilizadas

- **Python 3.x**
- **Pandas**: Manipulación y análisis de datos
- **NumPy**: Cálculo numérico
- **Matplotlib**: Visualización estática
- **Seaborn**: Visualización estadística
- **Plotly**: Visualizaciones interactivas
- **Jupyter Notebooks**: Entorno de desarrollo

---

## Conceptos Clave

> **Temperatura de equilibrio**: Temperatura de un planeta en la que la energía recibida desde su estrella se iguala a la emitida. En el caso de la Tierra T_eq = -18°C, que por el efecto invernadero asciende a +15°C.

> **Insolación**: Cantidad de radiación solar directa que recibe un planeta en un periodo determinado.

> **Zona Habitable**: Zona del espacio alrededor de una estrella en la que los planetas y satélites pueden albergar vida.

> **Metalicidad**: Abundancia relativa de elementos más pesados que el He. A mayor metalicidad, más joven es la estrella. Sirve para datar estrellas.

> **Tipo de estrella/tipo espectral**: Clasificación de las estrellas por su color (temperatura) y luminosidad (tamaño). El Sol es una estrella de tipo enana amarilla, tipo G/clase V.

> **Parsec**: Unidad de distancia. 1 pc = 30,856,804,799,935,500 m (~3.26 años luz).

### Clasificación Estelar

**Tipos Espectrales** (de más caliente a más frío):
- **O (Azules)**: >30,000 K - Muy masivas, raras y brillantes
- **B (Azules/Blancas)**: 10,000-30,000 K - Brillantes, helio ionizado
- **A (Blancas)**: 7,500-10,000 K - Líneas de hidrógeno fuertes
- **F (Blanco-Amarillas)**: 6,000-7,500 K
- **G (Amarillas)**: 5,200-6,000 K - Estrellas como el Sol
- **K (Naranjas)**: 3,500-5,200 K - Más frías y tenues que el Sol
- **M (Rojas)**: 2,500-3,500 K - Las más abundantes, muy frías

**Clases de Luminosidad** (Tamaño):
- **I**: Supergigantes
- **II**: Gigantes luminosas
- **III**: Gigantes
- **IV**: Subgigantes
- **V**: Secuencia Principal (enanas)

---

## Resultados Esperados

El análisis busca:
1. Identificar patrones en las características de exoplanetas descubiertos
2. Evaluar cuántos planetas cumplen criterios de habitabilidad
3. Comprender los sesgos en los métodos de detección actuales
4. Contextualizar la Paradoja de Fermi con datos empíricos
5. Proporcionar visualizaciones claras y atractivas para divulgación científica

---

## Cómo Ejecutar el Proyecto

1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/urkomen/proyectos.git
   cd proyectos/The_Bridge/2-EDA/src
   ```

2. **Instalar dependencias**:
   ```bash
   pip install pandas numpy matplotlib seaborn plotly jupyter
   ```

3. **Ejecutar los notebooks en orden**:
   - `EDA_definicion.ipynb` - Para entender el contexto del proyecto
   - `notebooks/dataset.ipynb` - Para obtener los datos
   - `notebooks/data_clean.ipynb` - Para limpiar los datos
   - `notebooks/analisis.ipynb` - Para realizar el análisis exploratorio

---

## Referencias

- [NASA Exoplanet Archive](http://exoplanetarchive.ipac.caltech.edu)
- [Planetary Systems Composite Data](https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=PSCompPars)
- Paradoja de Fermi y habitabilidad planetaria

---

<div align="center">
<em>"¿Dónde está todo el mundo?" - Enrico Fermi</em>
</div>
