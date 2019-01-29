
-- 1/ Récupérer tous les albums

SELECT Title FROM Albums;

-- 2/ Récupérer tous les albums dont le titre contient "Great"

SELECT Title FROM Albums WHERE Title LIKE '%Great%';

-- 3/ Donner le nombre total d'albums contenus dans la base (sans regarder les id bien sûr)

SELECT COUNT(*) FROM Albums;

-- 4/ Supprimer tous les albums dont le nom contient "music"
DELETE FROM Albums WHERE Title LIKE '%music%';

-- 5/ Récupérer tous les albums écrits par AC/DC
SELECT Title
FROM albums
INNER JOIN artists
ON artists.ArtistID = albums.ArtistID
WHERE Artists.Name LIKE '%AC/DC%';

-- 6/ Récupérer tous les titres des albums de AC/DC
SELECT tracks.Name
FROM tracks
INNER JOIN albums
ON tracks.AlbumID = albums.AlbumID
INNER JOIN artists
ON albums.ArtistId = artists.ArtistID
WHERE Artists.Name LIKE '%AC/DC%';

-- 7/ Récupérer la liste des titres de l'album "Let There Be Rock"
SELECT tracks.Name
FROM tracks
INNER JOIN albums
ON tracks.AlbumID = albums.AlbumID
WHERE Title LIKE '%Let There Be Rock%';

-- 8/ Afficher le prix de cet album ainsi que sa durée totale
SELECT SUM(Milliseconds), SUM(UnitPrice)
FROM tracks
INNER JOIN albums
ON tracks.AlbumID = albums.AlbumID
WHERE Title LIKE '%Let There Be Rock%';

-- 9/ Afficher le coût de l'intégralité de la discographie de "Deep Purple"
SELECT SUM(UnitPrice)
FROM tracks
INNER JOIN albums
ON tracks.AlbumID = albums.AlbumID
INNER JOIN artists
ON albums.ArtistId = artists.ArtistID
WHERE Artists.Name LIKE '%Deep Purple%';

-- 10/ Créer l'album de ton artiste favori en base, en renseignant correctement les trois tables albums, artists et tracks

INSERT INTO artists VALUES ('276', 'The Blaze');
INSERT INTO albums VALUES ('348', 'Dancehall', '276');
INSERT INTO tracks VALUES ('3504', 'Heaven', 
	(SELECT AlbumID FROM albums WHERE Title = 'Dancehall'),
	(SELECT MediaTypeId FROM media_types WHERE Name = 'MPEG audio file'),
	(SELECT GenreId FROM genres WHERE Name = 'Electronic'),
	'The Blaze', '8000', '198290', '20');

