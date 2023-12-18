go mod init
# install dbmate
sudo curl -fsSL -o /usr/local/bin/dbmate https://github.com/amacneil/dbmate/releases/latest/download/dbmate-linux-amd64
sudo chmod +x /usr/local/bin/dbmate
dbmate new todos
# create tables for todo db
CREATE TABLE `schema_migrations` (
  `version` varchar(255) COLLATE latin1_bin NOT NULL,
  PRIMARY KEY (`version`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 COLLATE=latin1_bin;

CREATE TABLE `todos` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `description` varchar(255) DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  `deleted_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
OCK TABLES `schema_migrations` WRITE;
INSERT INTO `schema_migrations` (version) VALUES  ('20211210045538'); #number when generate with dbmate new <tables>
UNLOCK TABLES;


go get github.com/gin-gonic/gin #-> go web framework
go get github.com/jinzhu/gorm #-> go ORM
go get gorm.io/driver/mysql  #-> go mysql driver
go get github.com/joho/godotenv #-> loads vars from .env file

============================================================
go run main.go

