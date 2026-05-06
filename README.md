# 🐝 FreTrack — Localisateur de nids de frelons asiatiques

> Application mobile PWA pour apiculteurs — triangulation de nids de *Vespa velutina* sur le terrain

![Licence](https://img.shields.io/badge/licence-MIT-green) ![PWA](https://img.shields.io/badge/PWA-ready-4a9e68) ![OpenStreetMap](https://img.shields.io/badge/carte-OpenStreetMap-blue) ![Sans clé API](https://img.shields.io/badge/API_key-aucune-brightgreen)

---

## 🎯 À quoi ça sert ?

Le frelon asiatique (*Vespa velutina nigrithorax*) est un prédateur redoutable pour les ruches. Pour réduire la pression sur vos colonies, la méthode la plus efficace reste la **destruction du nid à l'automne** — mais encore faut-il le trouver.

FreTrack vous aide à localiser les nids en exploitant deux informations récoltées sur les frelons que vous capturez et marquez au POSCA :

- 📐 **La direction de vol** au retour au nid (mesurée à la boussole du téléphone)
- ⏱ **Le temps aller-retour** (proportionnel à la distance du nid)

En combinant plusieurs observations, l'application triangule une **zone de recherche** directement sur une carte OpenStreetMap.

---

## 📱 Installation sur Android (sans Play Store)

1. Ouvrez l'URL de ce projet dans **Chrome sur Android**
2. Appuyez sur le menu ⋮ → **"Ajouter à l'écran d'accueil"**
3. Confirmez — FreTrack apparaît comme une vraie application

> ✅ Fonctionne hors-ligne une fois installée (sauf le chargement des tuiles de carte)

---

## 🚀 Fonctionnalités

### ⏱ Suivi multi-frelons simultané
Suivez jusqu'à 6 frelons **en parallèle** — chacun avec son propre chronomètre indépendant. Les slots sont nommés automatiquement selon la couleur de marquage POSCA : Jaune, Bleu, Rouge, Blanc, Vert, Orange.

- Démarrez le chrono au départ du frelon
- Stoppez-le à son retour
- **Le chrono continue en arrière-plan** pendant que vous enregistrez une direction

### 🧭 Boussole intégrée
Pointez le téléphone dans la direction de vol du frelon et appuyez sur son nom — la direction est enregistrée instantanément. Fonctionne pendant que le chrono tourne, sans interrompre le suivi.

### 🗺 Carte OpenStreetMap interactive
- Fond de carte réel avec chemins forestiers et bâtiments
- Rayons de direction tracés depuis votre position GPS
- Point de distance estimée par frelon (cliquable)
- **Marqueur 🐝 Nid ?** avec cercle d'incertitude
- Zoom et déplacement tactile

### 📊 Analyse automatique
- Direction moyenne (calcul vectoriel circulaire — pas de bug 0°/360°)
- Distance estimée basée sur la vitesse de vol de *V. velutina* (~8 km/h)
- Incertitude estimée à ±25%

### 💾 Données persistantes
Les observations sont sauvegardées en **localStorage** — elles survivent aux rechargements de page. Export CSV disponible pour archivage.

---

## 🔬 Méthode de triangulation

```
Distance estimée = (temps aller-retour ÷ 2) × 2,2 m/s
```

*Vespa velutina* vole en ligne droite vers son nid à environ **8 km/h (2,2 m/s)**. Un aller-retour de 2 minutes indique un nid à ~130 m.

Pour une triangulation précise :
- Capturez **au moins 5 individus** différents
- Si possible, répétez depuis **2 points distants de 30 à 50 m** pour croiser les rayons
- Les nids sont souvent dans les arbres de grande hauteur, en lisière de forêt

---

## 🛠 Technique

| Composant | Technologie |
|-----------|-------------|
| Interface | HTML/CSS/JS — PWA single file |
| Carte | [Leaflet.js](https://leafletjs.com/) + [OpenStreetMap](https://www.openstreetmap.org/) |
| Boussole | Web DeviceOrientation API |
| GPS | Web Geolocation API |
| Stockage | localStorage (données locales, aucun serveur) |
| Dépendances | Aucune (Leaflet chargé via CDN) |
| Clé API | **Aucune requise** |

> ⚠️ Le GPS et la boussole nécessitent une connexion **HTTPS** — c'est pourquoi l'app doit être hébergée (GitHub Pages, Netlify…) et non ouverte comme fichier local.

---

## 🌿 Contribuer

Les suggestions sont les bienvenues ! Idées en cours :

- [ ] Mode multi-points d'observation (triangulation depuis 2 positions GPS distinctes)
- [ ] Historique de sessions par date
- [ ] Export GPX pour import dans QGIS / Google Maps
- [ ] Mode nuit pour utilisation en conditions de faible luminosité

---

## 📜 Licence

MIT — libre d'utilisation, de modification et de partage.

---

<div align="center">
  <sub>Fait avec ❤️ par un apiculteur, pour les apiculteurs.<br>
  <i>Protégeons nos abeilles.</i> 🍯</sub>
</div>
