# music.db

CREATE TABLE Genres (
    genre_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL UNIQUE
);



CREATE TABLE Artists (
    artist_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL UNIQUE,
    country VARCHAR(100),
    debut_year INT
);


CREATE TABLE Albums (
    album_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    release_year INT,
    artist_id INT,
    genre_id INT,
    FOREIGN KEY (artist_id) REFERENCES Artists(artist_id),
    FOREIGN KEY (genre_id) REFERENCES Genres(genre_id)
);


CREATE TABLE Songs (
    song_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    duration TIME NOT NULL,
    album_id INT,
    artist_id INT,
    genre_id INT,
    FOREIGN KEY (album_id) REFERENCES Albums(album_id),
    FOREIGN KEY (artist_id) REFERENCES Artists(artist_id),
    FOREIGN KEY (genre_id) REFERENCES Genres(genre_id)
);


CREATE TABLE Playlists (
    playlist_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    created_at DATE
):

CREATE TABLE PlaylistSongs (
    playlist_id INT,
    song_id INT,
    PRIMARY KEY (playlist_id, song_id),
    FOREIGN KEY (playlist_id) REFERENCES Playlists(playlist_id),
    FOREIGN KEY (song_id) REFERENCES Songs(song_id)
):
