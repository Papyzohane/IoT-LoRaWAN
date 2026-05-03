🛰️ Surveillance Qualité de l'Air - SAE 3.01 (IoT & LoRaWAN)
📋 Présentation du Projet

Ce projet consiste en la conception et le déploiement d'une chaîne IoT complète pour la surveillance environnementale. L'objectif est de mesurer en temps réel le taux de CO2, la température et l'humidité, puis de transmettre ces données via un réseau basse consommation (LPWAN) pour les rendre accessibles sur une interface web publique.  

🛠️ Stack Technique

    Hardware : Microcontrôleur Seeeduino LoRaWAN + Capteur Sensirion SCD30.  

    Réseau : Protocole LoRaWAN via l'infrastructure The Things Network (TTN).  

    Backend : Webhooks TagoIO pour la gestion des données et alertes.  

    Frontend : Dashboard dynamique hébergé sur GitHub Pages (API TagoIO)

🏗️ Architecture et Fonctionnement de A à Z

Le système repose sur un flux de données structuré en cinq étapes majeures :
1. Acquisition Physique (Hardware)

    Capteur SCD30 : Utilisation d'un capteur de haute précision basé sur la technologie NDIR pour mesurer le CO2, complété par des sondes de température et d'humidité.  

    Microcontrôleur : Une carte Seeeduino LoRaWAN pilote le capteur via le protocole I2C.  

    Optimisation du Payload : Pour minimiser la consommation d'énergie, les données sont encodées en format binaire (hexadécimal) avant l'envoi, plutôt qu'en texte clair.  

2. Transmission Radio (LoRaWAN)

    Connectivité : Les données sont envoyées par modulation radio LoRa, idéale pour la longue portée.  

    Sécurisation OTAA : L'appareil utilise la méthode Over-the-Air Activation pour rejoindre le réseau de manière sécurisée, générant des clés de session uniques à chaque connexion.  

3. Gestion du Réseau (The Things Network)

    Collecte : Les trames radio sont captées par une gateway LoRaWAN et transmises aux serveurs de The Things Stack (TTN).  

    Payload Formatter : Un script JavaScript sur TTN décode les octets bruts pour reconstituer les valeurs numériques (ex: conversion de 0x01F4 en 500 ppm).  

4. Traitement Cloud et Alerting (TagoIO)

    Intégration : Les données décodées sont transmises instantanément à la plateforme TagoIO via un Webhook (requête HTTP POST).  

    Intelligence Embarquée : TagoIO stocke les données et exécute des actions automatiques, comme l'envoi d'un email d'alerte si le seuil de CO2 devient critique.  

5. Visualisation Web (Frontend)

    Dashboard : Création d'une interface de monitoring avec graphiques historiques sur TagoIO.  

    Déploiement : Une page web dynamique est hébergée sur GitHub Pages, communiquant avec l'API de TagoIO pour afficher les mesures en temps réel aux utilisateurs finaux.  

📂 Contenu du Dépôt

    /src : Code source Arduino (.ino).  

    /web : Interface utilisateur (HTML/CSS/JS).  

    /docs : Rapport technique et schémas.  

    payload_formatter.js : Script de décodage pour TTN.
