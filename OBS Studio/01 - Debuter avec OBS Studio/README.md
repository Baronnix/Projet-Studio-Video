# 🎥 Installation et configuration d’OBS Studio

Ce guide explique comment installer OBS Studio, créer tes sources, et configurer des scènes pour débuter dans le Streaming.

# 🎯 Objectif du tutoriel

Ce tutoriel a pour objectif de te guider pas à pas dans la création d’une configuration OBS Studio simple, propre et efficace pour enregistrer ou diffuser tes contenus.

Tu vas apprendre à :
* Installer OBS Studio sur ton ordinateur.
* Créer les sources essentielles : micro, capture d’écran, webcam, vidéo générique.
* Organiser tes scènes pour une utilisation fluide pendant tes enregistrements ou lives.
* Construire 3 scènes professionnelles adaptées à un workflow typique :
    * Scène 1 : Capture d’écran + webcam miniature en haut à droite + micro
    * Scène 2 : Générique seul
    * Scène 3 : Webcam + capture d’écran miniature en haut à droite + micro

À la fin du tutoriel, tu auras une configuration OBS prête à l’emploi, optimisée pour enregistrer des tutoriels, des présentations, des vidéos YouTube ou des sessions de streaming.

# 📺 Vidéo

Lien Youtube: [https://www.youtube.com/@Baronnix/playlists](https://www.youtube.com/@Baronnix/playlists)

# 🎥 Installation et configuration d’OBS Studio

1. Va sur le site officiel : obsproject.com
2. Télécharge la version Windows / macOS / Linux selon ton système.
3. Lance l’installateur et installe OBS Studio.
4. Ouvre OBS Studio.

Lors du premier lancement, OBS propose un Assistant de configuration automatique :
* Choisis Optimiser pour l’enregistrement ou Optimiser pour le streaming selon ton usage.
* Laisse OBS détecter les paramètres.

# 🎙️ Ajouter les sources essentielles

Chaque source est ajoutée pour une scène et peut s'utiliser dans plusieurs scènes.

## 1. Ajouter un micro

* Choisis une scène.
* Clique sur + dans Sources.
* Choisis Capture audio (entrée).
* Sélectionne ton micro (USB, casque, interface audio).
* Renomme la source : Micro Source.

## 2. Ajouter une capture d’écran

* Choisis une scène.
* Clique sur + dans Sources.
* Choisis Capture d'écran.
* Sélectionne ton écran.
* Renomme : Capture Écran Source.

## 3. Ajouter une webcam

* Choisis une scène.
* Clique sur + dans Sources.
* Choisis Périphérique de capture vidéo.
* Sélectionne ta webcam.
* Renomme : Webcam Source.
* Ajuste la taille en tirant les coins.

## 4. Ajouter une vidéo générique

* Choisis une scène.
* Clique sur + dans Sources.
* Choisis Média.
* Sélectionne ton fichier vidéo (intro, générique, animation).
* Renomme : Générique Source
* Coche Loop si tu veux qu’elle tourne en boucle.

# 🎬 Création des 3 scènes

## SCÈNE 1 — Capture écran + Webcam miniature en haut à droite + Micro

* Crée une nouvelle scène : Capture.
* Ajoute les sources suivantes:
    * Capture Écran Source
    * Webcam Source
    * Micro Source
* Modifie l'ordre des sources dans la scène pour avoir la Webcam par dessus la capture d' écran
* Rogner les bords de la vidéo
    * Clique droit sur la source Webcam
    * Aller dans Transformer -> Editer la transformation
    * Rogner les bords et confirmer
* Positionne la webcam :
    * Clique sur la source Webcam
    * Redimensionne pour faire une miniature
    * Déplace en haut à droite
* Vérifie que le micro apparaît dans le Mixer audio.

## SCÈNE 2 — Générique seul

* Crée une scène : Générique.
* Ajoute la source: Générique Source
* Coche Loop si tu veux un fond animé permanent.

## SCÈNE 3 — Webcam + miniature capture écran en haut à droite + Micro

Il est possible de dupliquer la scène 1 qui contient toutes les sources et de la modifier. 

Pour la créer de zéro:
* Crée une scène : Webcam.
* Ajoute :
    * Webcam Source
    * Capture Écran Source
    * Micro Source
* Modifie l'ordre des sources dans la scène pour avoir la Webcam par dessus la capture d' écran
* Positionne la capture d’écran :
    * Redimensionne
    * Place en haut à droite

# 🎛️ Conseils de configuration audio

Dans Mixer audio, clique sur ⚙️ → Filters :
* Ajoute Noise Suppression
* Ajoute Noise Gate
* Ajoute Compressor

Cela améliore énormément la qualité du micro.

# 🎨 Conseils de mise en page

* Utilise Ctrl + R pour réinitialiser la taille d’une source.
* Utilise Alt pour rogner une source (utile pour la webcam).
* Utilise Ctrl + S pour dupliquer une scène.
