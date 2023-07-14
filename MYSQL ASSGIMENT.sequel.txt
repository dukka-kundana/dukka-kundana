CREATE TABLE directors (
  director_id INT PRIMARY KEY,
  director_name VARCHAR(255)
);
INSERT INTO directors (director_id, director_name) VALUES
  (1, 'Director 1'),
  (2, 'Director 2'),
  (3, 'Director 3');
  CREATE TABLE movies (
  movie_id INT PRIMARY KEY,
  title VARCHAR(255),
  release_year INT,
  director_id INT,
  FOREIGN KEY (director_id) REFERENCES directors(director_id)
);
INSERT INTO movies (movie_id, title, release_year, director_id) VALUES
  (1, 'Movie 1', 2000, 1),
  (2, 'Movie 2', 2005, 2),
  (3, 'Movie 3', 2010, 3),
  (4, 'Movie 4', 2015, 1),
  (5, 'Movie 5', 2020, 2);
CREATE TABLE genres (
  genre_id INT PRIMARY KEY,
  genre_name VARCHAR(255)
);
INSERT INTO genres (genre_id, genre_name) VALUES
  (1, 'Genre 1'),
  (2, 'Genre 2'),
  (3, 'Genre 3');
  CREATE TABLE movie_genres (
  movie_id INT,
  genre_id INT,
  FOREIGN KEY (movie_id) REFERENCES movies(movie_id),
  FOREIGN KEY (genre_id) REFERENCES genres(genre_id)
);

INSERT INTO movie_genres (movie_id, genre_id) VALUES
  (1, 1),
  (1, 2),
  (2, 2),
  (3, 3),
  (4, 1),
  (5, 3);
  
  SELECT m.title, d.director_name
FROM movies m
JOIN directors d ON m.director_id = d.director_id;

SELECT m.title, m.release_year, d.director_name
FROM movies m
LEFT JOIN directors d ON m.director_id = d.director_id;

SELECT d.director_name, m.title
FROM directors d
LEFT JOIN movies m ON d.director_id = m.director_id;

SELECT m.title, m.release_year, d.director_name
FROM movies m
LEFT JOIN directors d ON m.director_id = d.director_id;

SELECT m.title, g.genre_name
FROM movies m
CROSS JOIN genres g;