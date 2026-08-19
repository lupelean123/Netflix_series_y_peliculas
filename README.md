# <p align="center">Netflix Series y películas</p>

<p align="center">
  <img src="image_netflix.jpeg" alt="Netflix" width="500"/>
</p>

**herramientas usadas:** Sqlite3

- **Problema de negocio:** Netflix quiere recabar información útil sobre sus series y películas para sus suscriptores a través de sus conjuntos de datos. El problema es que están trabajando con una cantidad excesiva de datos y no saben cómo analizarlos de manera efectiva ni cómo extraer información significativa de ellos. Necesitan una solución de análisis de datos robusta y escalable para manejar la cantidad de datos y descubrir patrones y tendencias valiosas.

- **Como puedo resolver el problema:** Para ayudar a Netflix a obtener información valiosa a partir de su extenso conjunto de datos sobre películas y series, utilizaré SQLite para extraer información relevante y realizar análisis detallados. Al aprovechar las funciones de SQL, podré identificar métricas clave como las calificaciones de los espectadores, las tendencias de popularidad, las preferencias de género y los patrones de audiencia.

## Questions I Wanted To Answer From the Dataset:
## 1. Which movies and shows on Netflix ranked in the top 10 and bottom 10 based on their IMDB scores?

- Top 10 Movies
```mysql
SELECT title, 
type, 
imdb_score
FROM shows_movies.titles
WHERE imdb_score >= 8.0
AND type = 'MOVIE'
ORDER BY imdb_score DESC
LIMIT 10
```
Result: 

<p align="center">
  <img src="imagenes/top 10 peliculas.png" alt="Netflix" width="400"/>
</p>

- Top 10 Shows
```mysql
SELECT title, 
type, 
imdb_score
FROM shows_movies.titles
WHERE imdb_score >= 8.0
AND type = 'SHOW'
ORDER BY imdb_score DESC
LIMIT 10
```
Result: 

<p align="center">
  <img src="imagenes/top 10 series.png" alt="Netflix" width="400"/>
</p
