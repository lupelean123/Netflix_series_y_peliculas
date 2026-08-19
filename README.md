# <p align="center">Netflix Series y películas</p>

<p align="center">
  <img src="image_netflix.jpeg" alt="Netflix" width="500"/>
</p>

**herramientas usadas:** Sqlite3

- **Problema de negocio:** Netflix quiere recabar información útil sobre sus series y películas para sus suscriptores a través de sus conjuntos de datos. El problema es que están trabajando con una cantidad excesiva de datos y no saben cómo analizarlos de manera efectiva ni cómo extraer información significativa de ellos. Necesitan una solución de análisis de datos robusta y escalable para manejar la cantidad de datos y descubrir patrones y tendencias valiosas.

- **Como puedo resolver el problema:** Para ayudar a Netflix a obtener información valiosa a partir de su extenso conjunto de datos sobre películas y series, utilizaré SQLite para extraer información relevante y realizar análisis detallados. Al aprovechar las funciones de SQL, podré identificar métricas clave como las calificaciones de los espectadores, las tendencias de popularidad, las preferencias de género y los patrones de audiencia.

## Primer paso: Conocer el Dataset

```mysql
SELECT COUNT(*) FROM titles
SELECT type, COUNT (*) FROM titles GROUP BY type
SELECT MIN (release_year) AS primer_año, MAX (release_year) AS ultimo_año FROM titles

```
<img width="134" height="65" alt="image" src="https://github.com/user-attachments/assets/179ecf06-4e98-43d0-aa05-bb84bb36008b" />
<img width="190" height="84" alt="image" src="https://github.com/user-attachments/assets/d2b207f2-641e-44ec-9a39-d53e96ec6a7b" />
<img width="197" height="59" alt="image" src="https://github.com/user-attachments/assets/faa22ce9-d1e7-40c5-a406-c25ea365c0e4" />



## 1. Which movies and shows on Netflix ranked in the top 10 and bottom 10 based on their IMDB scores?

- Top 10 Movies
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
Result: 

<p align="center">
  <img src="imagenes/top 10 peliculas.png" alt="Netflix" width="400"/>
</p>

- Top 10 Shows
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
Result: 

<p align="center">
  <img src="imagenes/top 10 series.png" alt="Netflix" width="400"/>
</p


## 2. How many movieesss... ? 

```mysql
SELECT CONCAT(FLOOR(release_year / 10) * 10, 's') AS decade,
	COUNT(*) AS movies_shows_count
FROM shows_movies.titles
WHERE release_year >= 1940
GROUP BY CONCAT(FLOOR(release_year / 10) * 10, 's')
ORDER BY decade;
```
Result: 

![Q5](https://i.ibb.co/8dTzVZ3/Screen-Shot-2023-07-09-at-10-02-18-PM.png)


## Conclusion 
By exploring .......... adasdsads. Fin. 
