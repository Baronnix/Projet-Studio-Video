# 📘 Optimiser les paramètres vidéo d’OBS Studio

Ce guide explique comment configurer OBS Studio pour :
* Streamer en 1280×720 (720p)
* Enregistrer en 1920×1080 (1080p)
* Configurer Twitch avec la clé de stream
* Exporter / importer une collection de scènes
* Exporter / importer ton profil OBS contenant les configurations

Cette configuration est idéale pour les créateurs qui veulent stream + enregistrer en même temps, avec une vidéo locale de haute qualité.

# 📺 Vidéo

Lien Youtube: [https://www.youtube.com/@Baronnix/playlists](https://www.youtube.com/@Baronnix/playlists)

# 🎥 1. Paramètres Vidéo : Base vs Sortie

OBS utilise deux résolutions :
 * Résolution de base (canvas) → ton espace de travail
 * Résolution de sortie → ce qui est réellement envoyé ou enregistré

## 🔧 Réglages recommandés

| Paramètre | Valeur | Raison |
|-------------------|------------------|-----------------------------------|
| Résolution de base | 1920×1080 | Qualité maximale pour les scènes |
| Résolution de sortie (stream) | 1280×720 | Débit plus faible, stream fluide |
| Résolution de sortie (enregistrement) | 1920×1080 | Vidéo nette pour YouTube |

# ⚙️ 2. Paramètres → Vidéo

1. Ouvre Paramètres → Vidéo
2. Configure :
    * Résolution de base : 1920×1080
    * Résolution de sortie : 1920×1080
    * FPS : 60

# 🎬 3. Paramètres → Sortie (Mode Avancé)

1. Ouvre Paramètres → Sortie
2. Configure :
    * Mode de sortie → Avancé

# 📡 4. Réglages du Streaming (# 1280×720)

1. Ouvre Paramètres → Sortie → Streaming
2. Configure :
    * Encodeur vidéo: x264
    * Mise à l'échelle pour la sortie: 
        * Lanczos
        * 1280x720
    * Débit vidéo : 4500–6000 kbps

# 💾 5. Réglages de l’Enregistrement (1920×1080)

1. Ouvre Paramètres → Sortie → Enregistrement :
2. Configure :
    * Type: Standard
    * Chemin d'accès de l'enregistrement: Le dossier d'enregistrement des vidéos
    * Format d'enregistrement: MP4 hybride (.mp4)
    * Encodeur vidéo: x264
    *  Mise à l'échelle pour la sortie: Désactivé

# 🔌 6. Configurer Twitch (clé de stream)

## 1️⃣ Récupérer ta clé de stream Twitch

1. Va sur ton tableau de bord Twitch
2. Ouvre Paramètres → Streaming
3. Copie la clé de streamin principale

## 2️⃣ Ajouter la clé dans OBS

1. Va dans OBS Studio
2. Ouvre Paramètres → Stream
3. Configure :
    * Service : Twitch
    * Méthode : connexion ou clé manuelle
    * Colle ta clé (si clé manuelle)

# 📦 7. Exporter / Importer une collection de scènes OBS

OBS permet d’exporter une collection de scènes sous forme de fichier .json.

## 📤 Exporter une collection de scènes

1. Menu Collection de scènes
2. Exporter
3. Choisis un nom → OBS génère un fichier .json

Ce fichier contient :
* Scènes
* Sources
* Filtres
* Groupes
* Transitions
* Layout complet

## 📥 Importer une collection de scènes

1. Menu Collection de scènes
2. Importer
3. Sélectionne ton fichier .json

OBS recrée automatiquement toutes les scènes

# 🧬 7. Exporter / Importer son profil OBS

OBS permet d’exporter son profil, c'est à dire les configurations.

## 📤 Exporter son profil

1. Menu Profil
2. Exporter
3. Choisis un dossier

Un dossier sera crée avec le nom de profil et contiendra les fichier de configuartion du profil.

## 📥 Importer son profil

1. Menu Profil
2. Importer
3. Sélectionne ton dossier de profil

OBS recrée automatiquement toutes les scènes

# 🚀 9. Workflow recommandé

* Stream → 1280×720
* Enregistrement → 1920×1080
* Export régulier de ta collection de scènes
* Sauvegarde réguliere du profil

Import rapide si tu changes de PC ou réinstalles OBS
