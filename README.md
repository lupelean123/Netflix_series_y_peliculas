# <p align="center">Netflix Series y películas</p>

<p align="center">
  <img src="image_netflix.jpeg" alt="Netflix" width="500"/>
</p>

**herramientas usadas:** Sqlite3

- **Problema de negocio:** Netflix quiere recabar información útil sobre sus series y películas para sus suscriptores a través de sus conjuntos de datos. El problema es que están trabajando con una cantidad excesiva de datos y no saben cómo analizarlos de manera efectiva ni cómo extraer información significativa de ellos. Necesitan una solución de análisis de datos robusta y escalable para manejar la cantidad de datos y descubrir patrones y tendencias valiosas.

- **Como puedo resolver el problema:** Para ayudar a Netflix a obtener información valiosa a partir de su extenso conjunto de datos sobre películas y series, utilizaré SQLite para extraer información relevante y realizar análisis detallados. Al aprovechar las funciones de SQL, podré identificar métricas clave como las calificaciones de los espectadores, las tendencias de popularidad, las preferencias de género y los patrones de audiencia.

## Primer paso: Exploración del Dataset

```mysql
PRAGMA table_info(titles) -- Info de la tabla general
SELECT COUNT(*) FROM titles -- Cantidad de registros
SELECT type, COUNT (*) FROM titles GROUP BY type -- Cantidad de series y peliculas
SELECT MIN (release_year) AS primer_año, MAX (release_year) AS ultimo_año FROM titles -- Años disponibles

```
### info de la tabla general
<img width="474" height="426" alt="image" src="https://github.com/user-attachments/assets/5c06703f-dd1e-482b-a30c-d3c970678b79" />

### Cantidad de registros
<img width="134" height="65" alt="image" src="https://github.com/user-attachments/assets/179ecf06-4e98-43d0-aa05-bb84bb36008b" />

### Cantidad de series (SHOWS) y peliculas (MOVIES)
<img width="190" height="84" alt="image" src="https://github.com/user-attachments/assets/d2b207f2-641e-44ec-9a39-d53e96ec6a7b" />

### Años disponibles
<img width="197" height="59" alt="image" src="https://github.com/user-attachments/assets/faa22ce9-d1e7-40c5-a406-c25ea365c0e4" />


En general se puede ver que dataset contiene 15 variables, Con 5.850 registros (filas) y los años de referencia de lanzamientos de las películas y series están entre 1945 y 2022, con un total de 3.744 peliculas y 2.106 series. 

## Ranking de peliculas y series del dataset

### top 10 peliculas

```mysql
SELECT title, 
type, 
imdb_score
FROM titles
WHERE imdb_score >= 8.0
AND type = 'MOVIE'
ORDER BY imdb_score DESC
LIMIT 10
```

<img width="468" height="296" alt="image" src="https://github.com/user-attachments/assets/5aef09aa-8351-42f1-b76f-8e48499a19f0" />

### top 10 series 

```mysql
SELECT title, 
type, 
imdb_score
FROM titles
WHERE imdb_score >= 8.0
AND type = 'SHOW'
ORDER BY imdb_score DESC
LIMIT 10
```

<img width="377" height="296" alt="image" src="https://github.com/user-attachments/assets/70a433e3-5483-481a-9013-6e343babe5c9" />

### top 10 peores peliculas

````mysql
SELECT title, 
type, 
imdb_score
FROM titles
WHERE type = 'MOVIE' AND imdb_score >= 0
ORDER BY imdb_score ASC
LIMIT 10
````
<img width="431" height="293" alt="image" src="https://github.com/user-attachments/assets/3696daf1-cce8-40dd-947b-21f5ab2ab2c5" />

### top 10 peores series

```mysql
SELECT title, 
type, 
imdb_score
FROM titles
WHERE type = 'SHOW' AND imdb_score >= 0
ORDER BY imdb_score ASC
LIMIT 10
```
<img width="434" height="296" alt="image" src="https://github.com/user-attachments/assets/613ded1a-62e5-4a00-9a38-88ab2c90ce21" />

explorando peliculas de interes:
```mysql
SELECT title, type, release_year, genres, production_countries, imdb_score, tmdb_score
FROM titles
WHERE type = 'MOVIE' AND release_year > 2015 AND production_countries = "['US']"
ORDER BY tmdb_score DESC
LIMIT 20
```
<img width="886" height="274" alt="image" src="https://github.com/user-attachments/assets/61df5ded-bd25-40dd-b09a-665d3ca34db9" />


 

Traducción realizada con la versión gratuita del traductor DeepL.com

## Conclusion 

La calificación de IMDb es un indicador ampliamente reconocido de la calidad general y la popularidad de una película o serie. Las 10 mejores películas y series se destacaron por sus excepcionales calificaciones en IMDb, lo que indica que gozan de gran reconocimiento entre los espectadores. Es probable que estos títulos hayan recibido gran reconocimiento y críticas positivas, lo que ha contribuido a su alta posición en el catálogo de Netflix.
Por otro lado, las 10 películas y series con peor desempeño obtuvieron puntuaciones más bajas en IMDb. Si bien es posible que estas propuestas no hayan tenido tanto impacto en el público, es importante señalar que hay muchos factores que influyen en estas clasificaciones, tales como las preferencias individuales, una trama débil, una actuación deficiente y una producción de baja calidad.
 Estos hallazgos pueden brindar información valiosa para los espectadores que buscan contenido altamente calificado y pueden servir como base para análisis posteriores y la toma de decisiones en las recomendaciones de Netflix para la audiencia.
