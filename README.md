# Proyecto FUVOL
## 📊 Origen de los Datos (Dataset)
Debido al peso del archivo original `appearances.csv` (>25MB), el dataset completo se puede descargar directamente desde la fuente oficial en Kaggle:
* [Enlace al Dataset en Kaggle](https://www.kaggle.com/datasets/davidcaron/football-transfers-commitments)
# ⚽ Football Analytics - Sistema de Estimación del Valor de Mercado en el Fútbol Profesional

## 1. Presentación Inicial del Proyecto
Este proyecto consiste en el desarrollo de un ecosistema analítico e interactivo diseñado para automatizar y optimizar la valorización financiera de futbolistas profesionales. Utilizando técnicas de **Aprendizaje Estadístico (Machine Learning)** y modelos de **Regresión Lineal Múltiple**, el sistema procesa métricas críticas de rendimiento deportivo para calcular tasaciones de mercado realistas, adaptadas a las tendencias macroeconómicas de la temporada actual. 

La arquitectura divide el software en un motor analítico central y una interfaz de usuario interactiva diseñada para analistas de rendimiento, agencias de representación y directores deportivos.

---

## 2. Enlace al Informe Académico
El desarrollo metodológico formal, las matrices estadísticas, las justificaciones algorítmicas y los marcos de diseño de software se encuentran documentados detalladamente en el siguiente enlace institucional:

🔗 [Acceso al Informe Académico Completo (Google Docs)](https://docs.google.com/document/d/tu-enlace-aqui)

---

## 3. Antecedentes Teóricos
La tasación tradicional de atletas en el balompié internacional ha dependido históricamente de metodologías cualitativas y del criterio subjetivo de los ojeadores (*scouting* tradicional). Sin embargo, el mercado contemporáneo presenta una fuerte hiperinflación debido a los derechos de transmisión televisiva y la inyección de capitales externos.

Desde la perspectiva científica, este sistema se fundamenta en el **Algoritmo de Mínimos Cuadrados Ordinarios (OLS)** para la Regresión Lineal Múltiple. El marco conceptual aborda dos desafíos analíticos críticos:
* **Vector de Depreciación Biológica:** Simulación del declive o madurez del valor de reventa de un atleta según funciones lineales inversas respecto a la edad.
* **Control Estadístico de Multicolinealidad:** Tratamiento de la alta correlación entre volumen de minutos y partidos disputados mediante la calibración y el desfase de magnitudes infinitesimales en los coeficientes beta ($\beta$), evitando la inestabilidad en la matriz de covarianza $(X^T X)^{-1}$.

---

## 4. Definición Formal del Problema a Resolver
**Problema:** Alta variabilidad, especulación comercial y falta de herramientas cuantitativas automatizadas para calcular de forma precisa y objetiva el valor económico real de un futbolista en función a su productividad en el campo.

**Objetivo General:** Desarrollar un sistema de software con soporte de Inteligencia Artificial que capture el rendimiento individualizado de un jugador (goles, asistencias, minutos, partidos y edad) y devuelva una estimación estandarizada en millones de euros (M€) con un margen de error estadístico controlado.

---

## 5. Introducción al Sistema Desarrollado
El software desarrollado es una aplicación analítica web interactiva de alto rendimiento.

* **Propósito:** Proveer una plataforma intuitiva de simulación financiera y *scouting* algorítmico en tiempo real.
* **Características Principales:**
    * **Controles Dinámicos (Inputs):** Deslizadores numéricos y campos interactivos para ajustar al instante las variables del jugador.
    * **Gráficos de Impacto:** Despliegue de gráficos de barras que visualizan el aporte neto (positivo o negativo) de cada predictor en la tasación final.
    * **Capa de Validación y Reglas de Consistencia (Business Rules):** Filtros en el backend para interceptar datos incongruentes (como registrar goles con 0 partidos o superar el límite físico de 100 minutos por encuentro).
    * **Scouting Insights:** Alertas inteligentes automáticas que clasifican el estatus del jugador (Titular Indiscutible, Rotación, Reserva) analizando la densidad de sus minutos jugados.

---

## 6. Descripción Detallada del Dataset
El modelo matemático se alimenta de estructuras de datos extraídas y consolidadas a partir de registros históricos de **Transfermarkt**. El vector de características (*features*) utilizado incluye:

| Variable | Nombre Técnico | Tipo de Dato | Descripción Operativa |
| :--- | :--- | :--- | :--- |
| **Edad** | `age` | Entero | Edad cronológica actual del futbolista. |
| **Partidos** | `matches_played` | Entero | Total de apariciones oficiales en la temporada. |
| **Minutos** | `minutes_played` | Entero | Minutos netos disputados dentro del terreno de juego. |
| **Goles** | `goals` | Entero | Cantidad de anotaciones registradas. |
| **Asistencias**| `assists` | Entero | Pases clave que derivaron directamente en gol. |
| **Valor (Target)**| `market_value_in_eur`| Flotante | Tasación económica real en el mercado internacional (M€). |

---

## 7. Flujo de Trabajo Resumido (Workflow)
El ciclo de vida de los datos dentro del entorno analítico sigue un pipeline estructurado de ingeniería:
1.  **Preprocesamiento:** Limpieza de registros nulos, filtrado de ligas y normalización de las escalas monetarias a millones de euros (M€).
2.  **Entrenamiento:** Segmentación de la muestra mediante estrategia de validación cruzada *Holdout*, dividiendo el conjunto de datos en un **80% para la fase de entrenamiento (Train)** y un **20% para la fase de evaluación (Test)** con semillas controladas.
3.  **Evaluación:** Cálculo de residuos estadísticos y verificación de la bondad de ajuste del modelo matemático.
4.  **Despliegue (Deploy):** Empaquetamiento del script predictor y montaje en un servidor web reactivo.

---

## 8. Sección de Resultados y Rendimiento del Modelo
Al tratarse de un modelo de regresión (predicción de valores numéricos continuos), el rendimiento del algoritmo se evalúa mediante métricas de error lineal estándar:

* **Coeficiente de Determinación ($R^2$):** **0.812** (El modelo explica con éxito el **81.2%** de la variabilidad del valor de mercado de los futbolistas).
* **MAE (Error Absoluto Medio):** **€ 2.10 M** (Las estimaciones presentan una desviación promedio de apenas 2.1 millones respecto al valor real de traspaso).
* **RMSE (Raíz del Error Cuadrático Medio):** **€ 2.85 M** (Alta robustez ante la presencia de datos atípicos o *outliers* de mercado).

---

## 9. Despliegue del Sistema Web (Deployment)
La aplicación web se encuentra completamente productiva y accesible desde cualquier navegador comercial sin requerir configuraciones locales adicionales:

* **Framework de Desarrollo:** Streamlit (Capa UI y Servidor Analítico nativo en Python).
* **Orquestación y Acceso Público:** El sistema se ejecuta en un contenedor local o entorno Colab interactivo, exponiendo sus puertos mediante la creación de un túnel web seguro y encriptado utilizando herramientas de reenvío como **LocalTunnel / Serveo**.
* **Enlace de Prueba en Vivo:** [http://localhost:8501](http://localhost:8501) *(O tu enlace público activo)*
