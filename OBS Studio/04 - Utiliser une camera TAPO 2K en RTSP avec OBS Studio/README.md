# 🎥 Intégrer une caméra TP-Link Tapo 2K dans OBS Studio (RTSP)

Tutoriel pour utiliser une caméra IP « de surveillance » abordable comme caméra de streaming/captation dans **OBS Studio**: flux vidéo en **RTSP**.

---

# 📺 Vidéo

Lien Youtube: [https://www.youtube.com/@Baronnix/playlists](https://www.youtube.com/@Baronnix/playlists)

---

## 1. 🚀 Objectif

- Utiliser une caméra IP **à bas coût** comme source vidéo dans **OBS Studio**.
- Récupérer le flux **en local** via **RTSP**, sans dépendre d’un service cloud.
- Valider la chaîne complète avec une **Tapo 2K** (modèle de test) avant d’investir éventuellement dans un modèle plus haut de gamme (Reolink E1 Zoom à zoom optique).

---

## 2. 📦 Prérequis

| Élément | Détail |
|---|---|
| Caméra | TP-Link Tapo 2K pan/tilt (ex. Tapo C210 / C220), firmware à jour |
| Application | **Tapo** (Android / iOS) pour l’installation initiale |
| Réseau | Caméra et PC d’OBS sur le **même réseau local** (idéalement en Ethernet ou Wi-Fi 5 GHz côté PC) |
| Routeur | Accès à l’interface pour **réserver une IP fixe (DHCP statique)** à la caméra |
| PC | Windows / macOS / Linux, CPU/GPU capable de décoder du H.264/H.265 |
| Logiciel | **OBS Studio** |

---

## 3. Comprendre les définitions vidéo : 2K, 3K, 4K, 5K

### 3.1 Tableau des définitions

| Appellation | Résolution typique | Mégapixels | Remarque |
|---|---|---|---|
| Full HD (1080p) | 1920 × 1080 | ~2 MP | Référence du streaming |
| **2K (QHD / 3 MP)** | 2304 × 1296 ou 2560 × 1440 | 3–4 MP | Le « 2K » marketing des caméras de surveillance |
| **3K (5 MP)** | 2880 × 1620 ou 2560 × 1920 | ~5 MP | |
| **4K (UHD / 8 MP)** | 3840 × 2160 | ~8 MP | 4× le 1080p |
| **5K** | 5120 × 2880 | ~14,7 MP | Rare sur caméras IP grand public |

> ⚠️ En surveillance, « 2K / 3K » sont des appellations marketing : vérifiez toujours la résolution réelle en pixels.

### 3.2 Pourquoi la résolution compte : zoom numérique vs zoom optique

- **Zoom optique** : les lentilles changent la focale. L’image est agrandie **sans perte de qualité**. La résolution de sortie reste pleine.
- **Zoom numérique** : on **recadre** une partie de l’image puis on l’agrandit. On perd des pixels.

**Règle pratique** pour une sortie OBS en **1080p** sans perte visible :

| Capteur | Zoom numérique « sans perte » vers 1080p |
|---|---|
| 1080p | ×1,0 (aucune marge) |
| 2K (2560 × 1440) | ≈ ×1,33 |
| 3K (2880 × 1620) | ≈ ×1,5 |
| 4K (3840 × 2160) | **×2** |
| 5K (5120 × 2880) | ≈ ×2,67 |

👉 Conclusion : pour faire du **zoom numérique** utile en 1080p, **au moins 3K** est nécessaire ; la **4K** donne un vrai ×2. Au-delà, seul un **zoom optique** garde la qualité.

> 💡 Attention aussi au **débit** : un flux 4K en RTSP demande plus de bande passante Wi-Fi et plus de décodage côté PC.

---

## 4. Cahier des charges pour le choix de la caméra

| # | Critère | Exigence | Pourquoi |
|---|---|---|---|
| 1 | **Protocole** | **RTSP** obligatoire (ONVIF fortement souhaité) | Ingestion directe dans OBS + pilotage PTZ |
| 2 | **Résolution** | **≥ 1080p**, **≥ 3K recommandé** | Marge pour le zoom numérique |
| 3 | **Connectivité** | **Wi-Fi + port Ethernet** | Ethernet = flux stable en direct |
| 4 | **Pan / Tilt motorisé** | Obligatoire | Cadrer à distance |
| 5 | **Zoom motorisé** | Optionnel (optique = idéal) | Qualité en gros plan |
| 6 | **Couverture** | Pan **360°**, tilt **> 80°** | Couvrir toute une pièce |
| 7 | **Compatibilité OBS** | Source média / VLC via RTSP | Intégration simple |
| 8 | **Pas de cloud obligatoire** | Fonctionnement **100 % local** | Confidentialité, latence, pérennité |
| 9 | **Prix** | **Abordable** (cible < 150 €) | Alternative aux caméras PTZ pro |

---

## 5. Caméras de streaming vs caméras de surveillance

Il existe de nombreuses caméras PTZ, mais les modèles **dédiés au streaming** (OBSBOT, PTZOptics, Logitech, Sony, Panasonic…) sont **chers** : de plusieurs centaines à plusieurs milliers d’euros, notamment ceux avec NDI, SDI ou VISCA.

À l’inverse, les **caméras de surveillance** motorisées grand public (TP-Link Tapo, Reolink…) coûtent **quelques dizaines d’euros**, proposent RTSP/ONVIF et un pan/tilt motorisé : elles semblent **compatibles** avec OBS pour un usage semi-pro (réunions, cours, captation, streaming simple).

Limites à connaître : latence RTSP (≈ 0,5–2 s), pas d’audio pro, moteurs PTZ bruyants et non progressifs, pas de NDI natif.

### Tableau comparatif

| Critère | **Tapo 2K** (C210/C220) | **Tapo 3K** (C230) | **Tapo 4K** (C260) | **Reolink E1 Zoom** |
|---|---|---|---|---|
| Résolution | 2K – 3/4 MP | 3K – 5 MP | 4K – 8 MP | 4K – 8 MP |
| Pan / Tilt | ✅ 360° / ~114° | ✅ 360° / ~114° | ✅ 360° / tilt large | ✅ 355° / 50° |
| Zoom | Numérique | Numérique | Numérique | **Optique ×3** |
| RTSP | ✅ (compte caméra) | ✅ | ✅ | ✅ |
| ONVIF (PTZ) | ✅ (port 2020) | ✅ | ✅ | ✅ |
| Wi-Fi | ✅ | ✅ | ✅ | ✅ (bi-bande) |
| Ethernet | ⚠️ selon modèle | ⚠️ selon modèle | ⚠️ à vérifier | ❌ Wi-Fi uniquement* |
| Cloud obligatoire | Compte Tapo pour l’installation, flux ensuite local | idem | idem | ❌ Non |
| Prix indicatif | ~25–40 € | ~40–60 € | ~60–90 € | ~80–120 € |
| Intérêt OBS | Test / budget | Bon compromis | Zoom numérique ×2 | Meilleure qualité de zoom |

\* Vérifier la fiche technique de la version exacte achetée. Les prix sont indicatifs et à vérifier au moment de l’achat.

---

## 6. Récapitulatif

| Modèle | Résolution | Pan/Tilt motorisé | Zoom | OBS / intérêt |
|---|---|---|---|---|
| Reolink E1 Zoom | **4K 8 MP** | ✅ | **Optique 3×** | ⭐⭐⭐⭐⭐ |
| Tapo C260 | **4K 8 MP** | ✅ | numérique | ⭐⭐⭐⭐ |
| Tapo C230 | **3K 5 MP** | ✅ | numérique | ⭐⭐⭐⭐ |
| Tapo C520WS | **2K QHD** | ✅ | numérique | plutôt extérieur |

---

## 7. Suivi du prix de la Reolink E1 Zoom (octobre → janvier)

Objectif : identifier le **meilleur moment d’achat**. Relever le prix chaque semaine (Amazon, boutique Reolink, Fnac/Darty…) ou utiliser un suivi automatique (Keepa, CamelCamelCamel, alerte prix).

| Date | Événement | Commentaire |
|---|---|---|
| 01/10 | Début de période | Prix de référence |
| ~08/10 | Prime Big Deal Days (Amazon) | 1ʳᵉ fenêtre promo |
| ~27/11 | **Black Friday** | Souvent le plus bas de l’année |
| ~30/11 | **Cyber Monday** | |
| 15/12 | Avant Noël | | Prix souvent remontés |
| ~07/01 | **Soldes d’hiver** (France) | 2ᵉ fenêtre promo |
| 31/01 | Fin de période | |

**Tendance attendue** (à confirmer par les relevés) : prix stable en octobre, **baisse marquée autour du Black Friday**, remontée en décembre, nouvelle baisse aux soldes de janvier.

![Estimation_Prix_Courbe](images/Estimation_Prix_Courbe.png)

👉 **Décision** : en attendant, on teste toute la chaîne avec la **Tapo 2K**.

---

## 8. Étape par étape : connecter la Tapo 2K dans OBS (vidéo RTSP)

### Étape 1 — Installer la caméra
1. Installer l’app **Tapo**, ajouter la caméra et la connecter au Wi-Fi (ou Ethernet).
2. Mettre à jour le **firmware**.

### Étape 2 — Créer le compte caméra (RTSP/ONVIF)
1. App Tapo → caméra → ⚙️ **Paramètres** → **Paramètres avancés** → **Compte de la caméra**.
2. Définir un **nom d’utilisateur** et un **mot de passe** dédiés (différents du compte TP-Link).

> Ce compte sert à la fois pour **RTSP** et **ONVIF**.

### Étape 3 — Fixer l’adresse IP
1. App Tapo → **Infos sur l’appareil** → noter l’**adresse IP**.
2. Dans le routeur, créer une **réservation DHCP** pour cette IP.
3. Associer la MAC à une IP, par ex. `192.168.1.50`.
4. Redémarrer la caméra et vérifier l'IP dans l'app.

| Box | Emplacement indicatif |
|---|---|
| Freebox | Paramètres de la Freebox → DHCP → Baux statiques |
| Livebox | Configuration avancée → Réseau → DHCP → Adresses IP statiques |
| SFR Box | Réseau → DHCP → Adresses IP fixes |
| Bbox | Services de la Box → DHCP → Adresses IP statiques |

### Étape 4 — Tester le flux dans VLC
**Média → Ouvrir un flux réseau** :

```text
rtsp://UTILISATEUR:MOTDEPASSE@192.168.1.50:554/stream1   # haute qualité (2K)
rtsp://UTILISATEUR:MOTDEPASSE@192.168.1.50:554/stream2   # basse qualité (360p/720p)
```

Si l’image s’affiche, le RTSP fonctionne.

### Étape 5 — Ajouter la source dans OBS
1. **Sources** → ➕ → **Source média** → nommer « Tapo 2K ».
2. ❌ Décocher **Fichier local**.
3. **Entrée** : `rtsp://UTILISATEUR:MOTDEPASSE@192.168.1.50:554/stream1`
4. **Format d’entrée** : `rtsp`
5. ✅ **Redémarrer la lecture quand la source devient active**
6. ✅ **Utiliser le décodage matériel si disponible**
7. **Taille du tampon réseau** : `1` à `2` Mo (réduire pour moins de latence).
8. **Délai de reconnexion** : `2` s.
9. Clic droit sur la source → **Transformer** → **Adapter à l’écran** (Ctrl+F).

> Alternative : source **Source vidéo VLC** (playlist avec l’URL RTSP) si la Source média saccade.

### Étape 6 — Optimiser

- Préférer **Ethernet** ou Wi-Fi 5 GHz pour le PC.
- Désactiver les options dans l’app.
- En cas de désynchronisation audio/vidéo : **Propriétés audio avancées** → ajouter un **décalage de synchronisation** sur le micro.
- Bloquer l'accès internet de la caméra

## 9. Bloquer l'accès internet de la caméra (Optionnel)

Objectif : la caméra fonctionne **uniquement en local** (Home Assistant), sans envoyer de flux vers le cloud.

> Faites-le **après** avoir tout configuré dans l'app (compte caméra, détection, mises à jour).

### Options (de la plus simple à la plus robuste)
1. **Contrôle parental / blocage d'appareil** de la box : bloquer l'accès internet pour la MAC de la caméra en conservant le réseau local.
2. **Pare-feu du routeur** (OpenWrt, pfSense, OPNsense, UniFi…) : règle `DROP` du trafic sortant WAN pour l'IP `192.168.1.50`.
3. **VLAN IoT dédié** : caméras isolées, internet bloqué, seul Home Assistant peut joindre la caméra (ports 554 et 2020, plus 443 pour Tapo Control).

### Conseils
- **Autoriser le NTP** (UDP 123) si possible, sinon l'horloge de la caméra peut dériver (horodatage incorrect).
- Réautoriser ponctuellement internet pour les **mises à jour de firmware**.
- Tester plusieurs jours la stabilité hors ligne.

### Ce que l'on perd
- Vue à distance et notifications via l'app Tapo (remplacées par Home Assistant).
- Mises à jour automatiques.

## 10. Dépannage

| Problème | Solution |
|---|---|
| Écran noir dans OBS | Tester l’URL dans VLC ; vérifier identifiants du **compte caméra** ; décocher « Fichier local » |
| Latence élevée | Réduire le tampon réseau, utiliser `stream1` en Ethernet, décodage matériel |
| Flux qui se coupe | Réserver l’IP, Wi-Fi plus proche, délai de reconnexion à 2 s |
| Image pixelisée en zoom | Limiter le zoom numérique ou passer à une caméra 4K / zoom optique |
| Accès impossible hors app | Mettre à jour le firmware ; recréer le compte caméra |

*Les caractéristiques et prix des caméras sont indicatifs : vérifiez la fiche technique officielle et la version exacte avant achat.*
