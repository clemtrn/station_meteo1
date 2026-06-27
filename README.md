Météo Xplorer

Version -- Juin 2026
Auteur -- Clémentine TRANNOY
Projet -- D2iP02 : Habib TALL, Jawaher TALL, Rémi TESSE, Clémentine TRANNOY, William SOUCHARD, Marguerite BLONDET

Ce dépôt contient la configuration et le code du serveur de la station météo connectée mobile MeteoXplorer. Ce serveur fait le pont entre l'ESP32 (acquisition) et le site web (visualisation).

Le serveur est développé avec Node-RED et hébergé sur la plateforme Render dans le Cloud pour assurer une disponibilité 24h/24. Il utilise un mécanisme de déploiement continu lié à ce dépôt GitHub.

La chaîne de traitement des données fonctionne ainsi :

- Réception : L'ESP32 transmet les mesures  via une requête HTTP POST contenant un fichier au format texte brut JSON
- Traduction : Un nœud Node-RED convertit ce texte JSON en un objet JavaScript
- Séparation : Le code sépare les valeurs en 13 variables  pour alimenter les graphiques
- Stockage et Distribution : Les fonctions global.set() et global.get() gèrent une base de données temporaire en mémoire pour répondre aux requêtes HTTP GET du site web (temps réel, historique et graphique)

Structure du Dépôt:

- package.json : Manuel d'instructions pour le déploiement sur Render

- flows.json : Sauvegarde des des nœuds Node-RED (les blocs et les fils)

- README.md : Ce guide explicatif
