# Bücher-Backend

### Datenbank erstellen

```bash
http://localhost/phpmyadmin
```

Datei [books-db.sql](./files/books-db.sql)

??? abstract "files/books-db.sql"
	``` mysql 
	-- phpMyAdmin SQL Dump
	-- version 5.0.2
	-- https://www.phpmyadmin.net/
	--
	-- Host: localhost
	-- Generation Time: Jul 15, 2020 at 02:36 PM
	-- Server version: 8.0.17
	-- PHP Version: 7.3.11

	SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
	START TRANSACTION;
	SET time_zone = "+00:00";


	/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
	/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
	/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
	/*!40101 SET NAMES utf8mb4 */;

	--
	-- Database: `books-db`
	--

	-- --------------------------------------------------------

	--
	-- Table structure for table `author`
	--

	CREATE TABLE `author` (
	  `author_id` int(11) NOT NULL,
	  `lastname` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL,
	  `firstname` varchar(255) NOT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

	--
	-- Dumping data for table `author`
	--

	INSERT INTO `author` (`author_id`, `lastname`, `firstname`) VALUES
	(1, 'Malcher', 'Ferdinand'),
	(2, 'Hoppe', 'Johannes'),
	(3, 'Kopenhagen', 'Danny'),
	(4, 'Zeigermann', 'Oliver'),
	(5, 'Hartmann', 'Nils'),
	(6, 'Bloch', 'Joshua');

	-- --------------------------------------------------------

	--
	-- Table structure for table `author_book`
	--

	CREATE TABLE `author_book` (
	  `id` int(11) NOT NULL,
	  `author_id` int(11) NOT NULL,
	  `book_id` int(11) NOT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

	--
	-- Dumping data for table `author_book`
	--

	INSERT INTO `author_book` (`id`, `author_id`, `book_id`) VALUES
	(1, 1, 1),
	(2, 2, 1),
	(3, 3, 1),
	(4, 4, 2),
	(5, 5, 2),
	(6, 6, 3);

	-- --------------------------------------------------------

	--
	-- Table structure for table `books`
	--

	CREATE TABLE `books` (
	  `book_id` int(11) NOT NULL,
	  `isbn` varchar(30) NOT NULL,
	  `title` varchar(50) NOT NULL,
	  `published` date NOT NULL,
	  `subtitle` varchar(255) NOT NULL,
	  `rating` smallint(6) NOT NULL,
	  `thumbnails` int(11) NOT NULL,
	  `description` varchar(255) NOT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

	--
	-- Dumping data for table `books`
	--

	INSERT INTO `books` (`book_id`, `isbn`, `title`, `published`, `subtitle`, `rating`, `thumbnails`, `description`) VALUES
	(1, '9783864906466', 'Angular', '2019-04-30', 'Grundlagen, fortgeschrittene Techniken und Best Practices - mit NativeScript und NgRx', 5, 1, 'Die Autoren führen Sie mit einem anspruchsvollen Beispielprojekt durch die Welt von Angular...'),
	(2, '9783864903274', 'React', '2016-06-17', 'Die praktische Einführung in React, React Router und Redux', 3, 2, 'React ist ein JavaScript-Framework zur Entwicklung von Benutzeroberflächen ...'),
	(3, '978-3-86490-578-0', 'Effective Java', '2018-09-01', 'Best Practices für die Java-Plattform', 3, 3, 'Seit der Vorauflage von Effective Java hat sich Java dramatisch verändert...');

	-- --------------------------------------------------------

	--
	-- Table structure for table `thumbnail`
	--

	CREATE TABLE `thumbnail` (
	  `id` int(11) NOT NULL,
	  `url` varchar(255) NOT NULL,
	  `title` varchar(255) NOT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

	--
	-- Dumping data for table `thumbnail`
	--

	INSERT INTO `thumbnail` (`id`, `url`, `title`) VALUES
	(1, 'https://ng-buch.de/cover2.jpg', 'Buchcover'),
	(2, 'https://ng-buch.de/cover1.jpg', 'Buchcover'),
	(3, 'https://www.dpunkt.de/common/images/cover_masterid/300/13216.jpg', 'Buchcover');

	--
	-- Indexes for dumped tables
	--

	--
	-- Indexes for table `author`
	--
	ALTER TABLE `author`
	  ADD PRIMARY KEY (`author_id`),
	  ADD KEY `author_id` (`author_id`);

	--
	-- Indexes for table `author_book`
	--
	ALTER TABLE `author_book`
	  ADD PRIMARY KEY (`id`),
	  ADD UNIQUE KEY `id` (`book_id`,`author_id`),
	  ADD KEY `author_id` (`author_id`);

	--
	-- Indexes for table `books`
	--
	ALTER TABLE `books`
	  ADD PRIMARY KEY (`book_id`),
	  ADD KEY `book_id` (`book_id`),
	  ADD KEY `thumbnails` (`thumbnails`);

	--
	-- Indexes for table `thumbnail`
	--
	ALTER TABLE `thumbnail`
	  ADD PRIMARY KEY (`id`);

	--
	-- AUTO_INCREMENT for dumped tables
	--

	--
	-- AUTO_INCREMENT for table `author`
	--
	ALTER TABLE `author`
	  MODIFY `author_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=7;

	--
	-- AUTO_INCREMENT for table `author_book`
	--
	ALTER TABLE `author_book`
	  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=7;

	--
	-- AUTO_INCREMENT for table `books`
	--
	ALTER TABLE `books`
	  MODIFY `book_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

	--
	-- AUTO_INCREMENT for table `thumbnail`
	--
	ALTER TABLE `thumbnail`
	  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

	--
	-- Constraints for dumped tables
	--

	--
	-- Constraints for table `author_book`
	--
	ALTER TABLE `author_book`
	  ADD CONSTRAINT `author_book_ibfk_1` FOREIGN KEY (`author_id`) REFERENCES `author` (`author_id`),
	  ADD CONSTRAINT `author_book_ibfk_2` FOREIGN KEY (`book_id`) REFERENCES `books` (`book_id`);

	--
	-- Constraints for table `books`
	--
	ALTER TABLE `books`
	  ADD CONSTRAINT `books_ibfk_1` FOREIGN KEY (`thumbnails`) REFERENCES `thumbnail` (`id`);
	COMMIT;

	/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
	/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
	/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
	```

### Node.js-Projekt erstellen

Ordner `books-backend` erstellen. In diesen Ordner wechseln. Im Ordner `npm init` ausführen (es entsteht eine `package.json`).

```bash
mkdir books-backend
cd books-backend
npm init
```

Alle Fragen mit einem `Enter` beantworten (oder etwas eingeben, wenn Sie möchten). Jetzt noch die Packages `express` und `mysql` installieren.

```bash
npm install express
npm install mysql
```

Im Ordner `books-backend` eine `index.js` erzeugen:

=== "books-backend/index.js"
	```javascript
	const express = require('express');
	const app = express();

	app.listen(8081, () => {
	    console.log('Server is listening to http://localhost:8081');
	});
	``` 

Im Ordner `books-backend` einen Ordner `books` erzeugen. Darin eine `index.js` (für den Router), eine `model.js` (für die Datenbankanbindung) und eine `controller.js` (für die Aktionsverwaltung) erstellen. Einen Endpunkt (`localhost/books/authors`) erstellen, um alle Authoren aus der Datenbank auszulesen (mit `GET`).

=== "/books/model.js"
	```javascript
	const mysql = require('mysql');
	const connection = mysql.createConnection({
	    host: 'localhost',
	    user: 'root',
	    password: 'password',
	    database: 'books-db',
	});

	connection.connect();

	function getAllAuthors() {
	    return new Promise((resolve, reject) => {
	        const query = 'SELECT * FROM author';
	        connection.query(query, (error, results) => {
	            if(error) reject(error);
	            else	  resolve(results);
	        })
	    });
	}

	module.exports = {
	    getAllAuthors,
	};
	```
=== "/books/controller.js"
	``` javascript
	const model = require('./model');

	function readAuthors(request, response) {
	    model.getAllAuthors().then(
	        authors => response.json(authors),
	        error => response.json(error),
	    );
	}

	module.exports = {
	    readAuthors,
	}
	```
=== "/books/index.js"
	``` javascript
	const express = require('express');
	const router = express.Router();
	const { readAuthors } = require('./controller');

	router.get('/authors', readAuthors);

	module.exports = router;
	```

Zum Testen in Postman:

``` bash
http://localhost:8081/books/authors
```

eingeben und `GET`-Methode wählen. Es erscheint das JSON mit allen Autoren:

??? abstract "Response-Body"
	``` json
	[
	    {
	        "author_id": 1,
	        "lastname": "Malcher",
	        "firstname": "Ferdinand"
	    },
	    {
	        "author_id": 2,
	        "lastname": "Hoppe",
	        "firstname": "Johannes"
	    },
	    {
	        "author_id": 3,
	        "lastname": "Kopenhagen",
	        "firstname": "Danny"
	    },
	    {
	        "author_id": 4,
	        "lastname": "Zeigermann",
	        "firstname": "Oliver"
	    },
	    {
	        "author_id": 5,
	        "lastname": "Hartmann",
	        "firstname": "Nils"
	    },
	    {
	        "author_id": 6,
	        "lastname": "Bloch",
	        "firstname": "Joshua"
	    }
	]
	```

#### GET - einen Autor auslesen

Neu hinzugekommener Code highlighted:

=== "/books/model.js"
	```javascript linenums="1" hl_lines="21-29 33"
	const mysql = require('mysql');
	const connection = mysql.createConnection({
	    host: 'localhost',
	    user: 'root',
	    password: 'password',
	    database: 'books-db',
	});

	connection.connect();

	function getAllAuthors() {
	    return new Promise((resolve, reject) => {
	        const query = 'SELECT * FROM author';
	        connection.query(query, (error, results) => {
	            if(error) reject(error);
	            else	  resolve(results);
	        })
	    });
	}

	function getOneAuthor(id) {
	    return new Promise((resolve, reject) => {
	        const query = 'SELECT * FROM author WHERE author_id=?';
	        connection.query(query, [id], (error, results) => {
	            if (error) reject(error);
	            else resolve(results[0]);
	        });
	    });
	}

	module.exports = {
	    getAllAuthors,
    	getAuthor(id) { return getOneAuthor(id) },
	};
	```
=== "/books/controller.js"
	``` javascript linenums="1" hl_lines="10-15 19"
	const model = require('./model');

	function readAuthors(request, response) {
	    model.getAllAuthors().then(
	        authors => response.json(authors),
	        error => response.json(error),
	    );
	}

	function readAuthor(request, response) {
	    model.getAuthor(request.params.id).then(
	        author => response.json(author),
	        error => response.status(500).json(error),
	    );
	}

	module.exports = {
	    readAuthors,
	    readAuthor,
	}
	```
=== "/books/index.js"
	``` javascript linenums="1" hl_lines="3 6"
	const express = require('express');
	const router = express.Router();
	const { readAuthors, readAuthor } = require('./controller');

	router.get('/authors', readAuthors);
	router.get('/author/:id', readAuthor);

	module.exports = router;
	```

Zum Testen in Postman z.B. `http://localhost:8081/books/author/4` (Autor mit der `author_id` 4) und `GET` aufrufen.

#### POST - einen neuen Autoren anlegen und PUT - einen Autoren ändern

Ein neuer Autor bzw. die Änderungen werden als JSON dem Request-Body übergeben. Dazu wird das Paket `body-parser` benötigt. 

``` bash
npm install body-parser
```


