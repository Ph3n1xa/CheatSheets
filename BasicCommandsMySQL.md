### 🔗 Connexion & Base
```Bash
mysql -u utilisateur -p            # Se connecter
mysql -h hôte -u utilisateur -p    # Se connecter à un serveur distant
SHOW DATABASES;                    # Lister les bases
USE nom_base;                      # Sélectionner une base
SELECT DATABASE();                 # Voir la base en cours
```
### 🏗️ Gestion des Bases
```SQL
CREATE DATABASE nom_base;
DROP DATABASE nom_base;
```
### 📂 Tables
```SQL
SHOW TABLES;                       # Voir les tables
DESCRIBE nom_table;                # Structure de la table
CREATE TABLE nom_table (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100),
    age INT
);
DROP TABLE nom_table;
```
### ✍️ Manipuler les Données
```SQL
INSERT INTO nom_table (nom, age) VALUES ('Alice', 25);
UPDATE nom_table SET age=26 WHERE nom='Alice';
DELETE FROM nom_table WHERE nom='Alice';
```
### 🔎 Sélectionner (SELECT)
```SQL
SELECT * FROM nom_table;                      # Tout afficher
SELECT nom, age FROM nom_table;               # Colonnes spécifiques
SELECT * FROM nom_table WHERE age > 20;       # Filtre
SELECT * FROM nom_table ORDER BY age DESC;    # Tri
SELECT COUNT(*) FROM nom_table;               # Compter les lignes
SELECT AVG(age) FROM nom_table;               # Moyenne
```
### 🔗 Jointures
```SQL
SELECT u.nom, p.produit
FROM utilisateurs u
JOIN achats p ON u.id = p.user_id;
```
### 👮 Gestion Utilisateurs
```SQL
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON base.* TO 'user'@'localhost';
FLUSH PRIVILEGES;
```
### 💾 Sauvegarde / Restauration
```Bash
mysqldump -u utilisateur -p nom_base > backup.sql   # Sauvegarde
mysql -u utilisateur -p nom_base < backup.sql      # Restaure
```
---
