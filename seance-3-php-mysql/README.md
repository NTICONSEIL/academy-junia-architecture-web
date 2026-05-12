# 🐘 Séance 3 — PHP et MySQL

> **Durée :** 8h | **Statut :** 🚧 En préparation

---

## 🎯 Objectifs prévisionnels

À l'issue de cette séance, les étudiants seront capables de :

- Écrire du **PHP** de base : variables, structures de contrôle, fonctions
- Traiter des **formulaires** côté serveur (`GET` et `POST`, `$_POST`, `$_FILES`)
- Se connecter à une **base de données MySQL** et exécuter des requêtes
- Gérer l'**authentification** des utilisateurs (sessions, cookies)
- **Brancher** le formulaire CV de la séance 2 sur un back-end fonctionnel

---

## 📋 Plan prévisionnel

### Partie 1 — PHP : les bases
- Syntaxe, variables, types
- Structures de contrôle (`if`, `for`, `while`, `foreach`)
- Fonctions, tableaux, chaînes
- Inclusions (`include`, `require`)

### Partie 2 — PHP et HTTP
- Transmission des données (`GET` vs `POST`)
- Récupération des champs de formulaire
- Upload de fichiers (`$_FILES`)
- Sécurité : validation et échappement des entrées

### Partie 3 — PHP et MySQL
- Connexion à la base (`mysqli` ou `PDO`)
- Requêtes préparées (protection contre l'injection SQL)
- CRUD : insertion, lecture, mise à jour, suppression
- Conception du schéma de la base CV

### Partie 4 — Sessions et cookies
- Principe des sessions
- Authentification étudiant / entreprise / admin
- Cookies (préférences, "se souvenir de moi")

### Partie 5 — TP : brancher le formulaire CV sur la base
- API JSON côté serveur (`api/enregistrer-cv.php`, `api/profils.php`)
- Reprise du `fetch` de la séance 2
- Page d'accueil avec catalogue dynamique

---

## 📎 Supports à venir

- 📄 `memo-php.md` — Mémo complet PHP
- 📄 `memo-mysql.md` — Mémo MySQL et requêtes préparées
- 📄 `tp-3-cv-back-end.md` — TP de connexion front/back
- 🗃️ `bdd-cv.sql` — Script de création de la base de données

---

## 🛠️ Outils prévus

- **XAMPP** : Apache + PHP + MySQL en local
- **phpMyAdmin** : interface graphique pour MySQL
- **Postman** ou onglet **Network** du navigateur : pour tester les API

---

## 🔗 Liens

- Séance précédente : [📁 seance-2-css-js](../seance-2-css-js/)
- Plan de cours global : [📄 plan-de-cours.md](../plan-de-cours.md)
- Projet final : [📁 projet-final](../projet-final/)
