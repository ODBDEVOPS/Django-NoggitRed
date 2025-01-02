# Django-NoggitRed ODBDEVOPS! 👋
🔭 Refaire un modèle capable de reproduire ce que fait Noggit Red (un éditeur de cartes pour World of Warcraft) dans une application Django est un projet extrêmement ambitieux, mais théoriquement possible. Cependant, cela nécessiterait de combiner Django avec des technologies front-end avancées pour gérer les aspects graphiques et 3D.

💬 Ask

## 🛠️ Technologies & Tools
<p align="left">
  <img src="https://img.shields.io/badge/Django-3776AB?style=flat&logo=python&logoColor=white" alt="Django"/>
</p>

# 1. Analyse des fonctionnalités de Noggit Red
Noggit Red permet de :
- Charger et visualiser des cartes du jeu (basées sur des fichiers de terrain et d'objets 3D).
- Modifier le terrain (hauteur, texture, etc.).
- Ajouter ou supprimer des objets.
- Sauvegarder les modifications dans un format compatible avec World of Warcraft.

Reproduire ces fonctionnalités implique :
- Un backend capable de lire et écrire les fichiers du jeu (par exemple, les fichiers .ADT, .WMO, ou .M2).
- Un frontend capable de rendre des modèles 3D en temps réel, d'appliquer des textures et d'interagir avec l'utilisateur.

# 2. Rôle de Django
Django peut jouer un rôle crucial dans le backend :
- Gestion des fichiers : Django peut être utilisé pour uploader, lire, et servir les fichiers nécessaires.
- API RESTful : Django REST Framework (DRF) peut exposer des endpoints permettant au frontend d'interagir avec les fichiers du jeu (lecture, modification, sauvegarde).
- Authentification et permissions : Django peut gérer les utilisateurs, les projets, et les autorisations.
- Stockage des données : Utiliser une base de données pour enregistrer des métadonnées sur les cartes et les modifications.


# 3. Technologies front-end pour la visualisation 3D
Pour la partie front-end, Django devra être complété par une bibliothèque ou un moteur 3D capable de gérer les fonctionnalités en temps réel.
  Options populaires :
  - Three.js : Une bibliothèque JavaScript pour rendre des objets 3D dans le navigateur.
  - Babylon.js : Une alternative puissante à Three.js, conçue pour des expériences interactives.
  - Unity WebGL : Une solution plus avancée, mais qui nécessiterait d'intégrer Unity dans une application Django.

Ces outils peuvent gérer le rendu 3D des fichiers convertis depuis le format natif de World of Warcraft (comme les fichiers .ADT ou .WMO).

# 4. Pipeline pour la manipulation des fichiers

Les fichiers du jeu World of Warcraft utilisent des formats propriétaires. Voici un pipeline possible pour les manipuler avec Django :

## 1. Extraction et conversion des fichiers :
- Utiliser des bibliothèques externes comme CascView pour extraire les fichiers du client WoW.
- Convertir les fichiers .ADT, .WMO, ou .M2 dans des formats compatibles avec les outils de manipulation 3D (comme .obj ou .gltf).
## 2. Backend pour la lecture et la modification :
- Développer des outils Python capables de lire et d'éditer ces fichiers (ex. : utiliser des bibliothèques comme pywowlib ou en créer une dédiée).
- Exposer ces fonctionnalités via des API REST.
## 3. Frontend pour l'édition en temps réel :
- Charger les modèles et les terrains dans un visualiseur 3D basé sur Three.js ou Babylon.js.
- Implémenter des outils d'édition (changement de texture, modification de hauteur, placement d'objets).
- Envoyer les modifications au backend pour mise à jour des fichiers source.

# 5. Exemple de flux de travail Django/Three.js
## 1. Backend Django :
- Une vue pour uploader une carte (fichier .ADT).
- Un endpoint REST pour retourner les données de la carte converties en JSON (ex. : géométrie, textures).
- Une vue pour sauvegarder les modifications.
## 2. Frontend avec Three.js :
- Récupérer la carte via l'API REST.
- Afficher le terrain en 3D.
- Ajouter des outils d'édition (ex. : glisser pour modifier la hauteur, appliquer des textures).


