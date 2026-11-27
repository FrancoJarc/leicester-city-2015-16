# 🏆 Leicester City 2015/16: Análisis de una temporada histórica

## 📖 Descripción del proyecto

En la temporada 2015/16, Leicester City protagonizó una de las mayores sorpresas en la historia del deporte al conquistar la Premier League inglesa. Un equipo que había luchado por evitar el descenso la temporada anterior logró superar a clubes como Arsenal, Manchester City, Manchester United y Tottenham para convertirse en campeón.

El objetivo de este proyecto es analizar los datos de la temporada 2015/16 para responder una pregunta principal:

> ¿Cómo logró Leicester City ganar la Premier League 2015/16?

Para responderla se realizó un análisis exploratorio de datos con Python y Pandas, estudiando el rendimiento del equipo desde distintas perspectivas: resultados, ataque y defensa, comparación con sus rivales, desempeño como local y visitante, eficiencia de cara al arco, expectativas de las casas de apuestas y evolución a lo largo de la temporada.

## ⚡ Resumen

- **Regularidad:** perdió solo 3 de 38 partidos, la menor cantidad de la liga.
- **Rendimiento en todas las condiciones:** fue el mejor local y el mejor visitante del campeonato.
- **Eficiencia:** tuvo la mejor conversión de tiros de la liga (13%, contra un promedio de 10.5%).
- **Superó al mercado:** según las cuotas de Bet365 se esperaban 53.3 puntos y sumó 81, la mayor diferencia de la liga.

![Puntos esperados y obtenidos](images/puntos_esperados_vs_reales.png)

---

## 🎯 Objetivos

- Analizar el rendimiento general de Leicester City durante la temporada 2015/16.
- Comparar sus estadísticas con las de sus principales competidores.
- Evaluar su rendimiento como local y como visitante.
- Medir su eficiencia ofensiva.
- Contrastar sus resultados con las expectativas de las casas de apuestas (Bet365).
- Analizar cómo se construyó el título a lo largo de la temporada.
- Identificar los factores que explican la obtención del campeonato.

---

## 🛠️ Tecnologías utilizadas

- Python
- Pandas
- Matplotlib
- Jupyter Notebook
- Git & GitHub

---

## 📊 Dataset

- **Fuente:** paquete [English Premier League](https://datahub.io/sports-data/english-premier-league) de datahub.io, que recopila los datos de [football-data.co.uk](http://www.football-data.co.uk/).
- **Licencia:** Open Data Commons Public Domain Dedication and License (PDDL) v1.0.
- **Archivo utilizado:** `data/season-1516_csv.csv`
- **Tamaño:** 380 partidos (20 equipos, 38 fechas) y 65 columnas.

Cada registro representa un partido e incluye:

- Equipos participantes y fecha
- Goles (al final y al entretiempo) y resultado
- Tiros totales y tiros al arco
- Faltas, córners y tarjetas
- Cuotas de distintas casas de apuestas

---

## ✅ Calidad de los datos

Antes del análisis se validó lo siguiente:

- No hay registros duplicados.
- El resultado registrado (local, empate o visitante) coincide con los goles en los 380 partidos.
- No hay valores negativos en goles, tiros, faltas, córners ni tarjetas.
- Los únicos valores nulos son tres cuotas de Betway (BWH, BWD, BWA) del partido Tottenham–Newcastle del 13/12/2015. Se conservó el registro porque el análisis usa las cuotas de Bet365, no las de Betway.
- Se encontró una inconsistencia: en Aston Villa vs. West Ham (26/12/2015), Aston Villa registra más tiros al arco (8) que tiros totales (5). Se conservó el registro sin modificar, porque no es posible saber qué valor es el incorrecto. No afecta a Leicester. Sí entra en el gráfico de tiros de toda la liga, pero Aston Villa es el equipo con menos tiros y goles del campeonato, y una diferencia de pocos tiros no cambia su posición en el gráfico.

---

# 🔍 Principales hallazgos

## 1. Regularidad por encima de todo

Leicester finalizó la temporada con:

| Métrica | Valor |
|----------|----------|
| Puntos | 81 |
| Victorias | 23 |
| Empates | 12 |
| Derrotas | 3 |
| Goles a favor | 68 |
| Goles en contra | 36 |

Ganó la liga con 10 puntos de ventaja sobre Arsenal. El dato más destacado es que solo perdió 3 partidos, la menor cantidad del campeonato, mientras que los equipos que terminaron del 2° al 5° puesto registraron entre 6 y 10 derrotas.

![Derrotas por equipo](images/derrotas_por_equipo.png)

---

## 2. No fue el mejor ataque ni la mejor defensa

Leicester no lideró ninguna de las dos estadísticas, pero estuvo entre los mejores en ambas:

- **Ataque:** 68 goles, el tercero más goleador detrás de Manchester City (71) y Tottenham (69).
- **Defensa:** 36 goles recibidos, igual que Arsenal. Solo Tottenham y Manchester United recibieron menos (35).

---

## 3. Rendimiento equilibrado como local y visitante

| Condición | Puntos | Goles a favor | Goles en contra |
|------------|------------|------------|------------|
| Local | 42 | 35 | 18 |
| Visitante | 39 | 33 | 18 |

Leicester sumó casi la misma cantidad de puntos y goles en ambas condiciones, y recibió exactamente los mismos goles de local que de visitante.

Además, fue el mejor equipo de la liga en las dos condiciones, pero la diferencia fue mucho mayor de visitante: sumó 39 puntos fuera de casa, 5 más que Tottenham (34), mientras que de local superó por solo un punto a Manchester United (42 contra 41).

![Puntos de local y de visitante](images/puntos_local_visitante.png)

---

## 4. Fue el equipo más eficiente de la liga

Comparación con los equipos que terminaron del 2° al 5° puesto:

| Equipo | Goles | Tiros | Conversión |
|----------|----------|----------|----------|
| Leicester | 68 | 523 | 13.00% |
| Arsenal | 65 | 572 | 11.36% |
| Tottenham | 69 | 661 | 10.44% |
| Manchester City | 71 | 612 | 11.60% |
| Manchester United | 49 | 430 | 11.40% |

*Conversión = goles / tiros totales.*

Leicester registró la mejor tasa de conversión entre estos equipos y también de toda la liga, cuyo promedio fue 10.51%. Con 138 tiros menos que Tottenham, terminó la temporada con solo un gol menos.

![Tiros y goles por equipo](images/tiros_vs_goles.png)

---

## 5. Superó las expectativas del mercado durante toda la temporada

A partir de las cuotas de Bet365 se calcularon los **puntos esperados** de cada equipo: la probabilidad implícita de cada resultado (1 / cuota), ajustada por el margen de la casa de apuestas, se convierte en puntos esperados por partido (3 × P(victoria) + 1 × P(empate)) y se suma en los 38 partidos.

| Equipo | Puntos esperados | Puntos obtenidos | Diferencia |
|----------|----------|----------|----------|
| Leicester | 53.3 | 81 | +27.7 |
| West Ham | 46.6 | 62 | +15.4 |
| Tottenham | 65.0 | 70 | +5.0 |
| Arsenal | 74.0 | 71 | -3.0 |
| Manchester City | 75.9 | 66 | -9.9 |

Leicester fue, por lejos, el equipo que más superó lo que esperaba el mercado (ver el gráfico del resumen).

Las casas de apuestas ajustaron sus expectativas a medida que avanzaba la temporada, pero Leicester siguió superándolas:

| Mitad de la temporada | Partidos como favorito | Prob. promedio de ganar | Puntos esperados | Puntos obtenidos |
|----------|----------|----------|----------|----------|
| Partidos 1 a 19 | 7 de 19 | 34% | 24.4 | 39 |
| Partidos 20 a 38 | 14 de 19 | 42% | 28.8 | 42 |

*Se consideró favorito a un equipo cuando su cuota de victoria era menor que la de su rival.*

---

## 6. Tomó la punta en la segunda mitad y no la soltó

Comparando los puntos acumulados partido a partido, Leicester tuvo menos puntos que Arsenal o Tottenham después de sus partidos 7 a 12 y del partido 20. Desde el partido 21 fue siempre el que más puntos sumaba de los tres, y terminó con 10 puntos de ventaja.

![Puntos acumulados](images/puntos_acumulados.png)

---

# 🏁 Conclusión

Los datos indican que Leicester City no ganó la Premier League 2015/16 por dominar una estadística específica, sino por combinar regularidad, equilibrio y eficiencia.

No fue el equipo más goleador ni el que menos goles recibió, pero se mantuvo entre los mejores en ambas facetas y fue el que menos partidos perdió. Fue el mejor local y el mejor visitante de la liga, con una ventaja mayor fuera de casa, y necesitó menos tiros que sus rivales directos para marcar una cantidad de goles parecida.

Además, sumó 27.7 puntos más de los que esperaba el mercado, la mayor diferencia de la liga, y lo hizo en las dos mitades de la temporada, incluso después de que las casas de apuestas empezaran a considerarlo favorito. Tomó la punta a partir de su partido 21 y no la volvió a perder.

---

## ⚠️ Limitaciones

- Se analiza una sola temporada (38 partidos de Leicester), por lo que las diferencias entre equipos pueden estar influidas por la variabilidad propia de una muestra chica.
- El dataset no incluye métricas de calidad de las ocasiones (como goles esperados o xG). Por eso, una tasa de conversión alta no permite distinguir entre calidad de definición y variabilidad.
- La definición de favorito compara solo las cuotas de victoria de ambos equipos y no tiene en cuenta la cuota del empate.
- Los puntos esperados se calculan con las cuotas de una sola casa de apuestas (Bet365) y con un ajuste proporcional del margen, que es el método más simple. Otros métodos de ajuste pueden dar valores levemente distintos.

---

## 📁 Estructura del repositorio

```
leicester-city-2015-16/
├── data/
│   ├── season-1516_csv.csv     # Dataset de la temporada 2015/16
│   ├── datapackage.json        # Metadatos y licencia de la fuente
│   └── processed/
│       └── team_matches.csv    # Una fila por equipo por partido, exportada para Tableau
├── images/                     # Gráficos generados por el notebook
├── notebooks/
│   └── analysis.ipynb          # Análisis completo
└── README.md
```

---

## ▶️ Cómo ejecutarlo

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/FrancoJarc/leicester-city-2015-16.git
   cd leicester-city-2015-16
   ```
2. Instalar las dependencias:
   ```bash
   pip install pandas matplotlib jupyter
   ```
3. Abrir `notebooks/analysis.ipynb` y ejecutar todas las celdas en orden (Restart & Run All).

---

## 👤 Autor

**Franco Jarc** · [GitHub](https://github.com/FrancoJarc)
