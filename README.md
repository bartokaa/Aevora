 <div align="center">

# Aevora

**Animated wallpapers for Windows**

Un projet de logiciel de fonds d'écran animés pour Windows.

<br>

![Windows](https://img.shields.io/badge/Platform-Windows-0078D4?style=flat-square&logo=windows&logoColor=white)
![C++17](https://img.shields.io/badge/C%2B%2B-17-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![V4](https://img.shields.io/badge/Engine-V4%20functional-2ea44f?style=flat-square)
![V4.1](https://img.shields.io/badge/Next%20version-V4.1-7657D5?style=flat-square)
![Release](https://img.shields.io/badge/Public%20release-Not%20available-gray?style=flat-square)

[About](#about) · [Development](#development) · [Roadmap](#roadmap) · [Français](#français)

</div>

---

## About

Aevora is a project I'm working on to create an animated wallpaper application for Windows.

I'm building the engine in C++ using native Windows technologies for video playback and desktop integration.

The V4 engine is functional. It has been tested, its temporary diagnostics have been removed, and a new backup has been created before moving on to V4.1.

The project is still in development, and there isn't a public release yet.

## Development

### V4 — Engine

<img src="https://img.shields.io/badge/Status-Functional-2ea44f?style=for-the-badge" alt="V4 functional" />

The main engine is working and has been tested.

| Feature | Status |
|:---|:---:|
| MP4 / H.264 video playback | ✅ |
| Hardware decoding when available | ✅ |
| Video format handling and fallback | ✅ |
| Automatic video looping | ✅ |
| More than 10 consecutive loop cycles tested | ✅ |
| Clean shutdown with `--stop` | ✅ |
| Single-instance protection | ✅ |
| Windows desktop integration | ✅ |
| Recovery after Explorer restarts | ✅ |
| Session lock and unlock handling | ✅ |
| Display resolution changes | ✅ |
| Health checks every 5 seconds | ✅ |
| Temporary pixel diagnostics removed | ✅ |
| Successful compilation after cleanup | ✅ |
| Stable backup created and checked | ✅ |

<details>
<summary><strong>Known issues</strong></summary>

These are the issues I've identified that still need attention.

- [ ] Fix the loop retry counter, which currently resets and can repeatedly display attempt 1/3.
- [ ] Implement the Fit and Stretch scaling modes. The current rendering behaves like Fill.
- [ ] Investigate the two remaining D3D11 device references at shutdown.
- [ ] Add keyframe detection if precise video seeking becomes necessary.
- [ ] Improve Visual Studio Build Tools detection instead of relying on a hard-coded path.

</details>

---

## Roadmap

### V4.1 — What's next?

Here's what I plan to work on next.

<details open>
<summary><strong>01 — Engine improvements</strong></summary>

- [ ] Fix the loop retry counter.
- [ ] Implement Fit, Fill and Stretch correctly.
- [ ] Clean up the remaining D3D11 references.

</details>

<details open>
<summary><strong>02 — Wallpaper library</strong></summary>

- [ ] Scan a local folder for videos.
- [ ] Allow switching between wallpapers.
- [ ] Add support for local playlists.
- [ ] Explore locally available Steam Workshop content without integrating the Steamworks API in this phase.

</details>

<details open>
<summary><strong>03 — Settings</strong></summary>

- [ ] Add a basic configuration interface.
- [ ] Choose a wallpaper.
- [ ] Change the scaling mode.
- [ ] Enable or disable looping.
- [ ] Adjust the volume.

</details>

<details>
<summary><strong>04 — Other improvements</strong></summary>

- [ ] Add log levels and automatic log rotation.
- [ ] Add optional support for secondary monitors.
- [ ] Test the new features.

</details>

---

## Progress

| Milestone | Status |
|:---|:---|
| V4 engine | ✅ Functional |
| Video playback and looping | ✅ Tested |
| Desktop integration | ✅ Implemented |
| Diagnostic cleanup | ✅ Completed |
| Successful recompilation | ✅ Verified |
| Stable backup | ✅ Created and checked |
| V4.1 improvements | 🔄 Planned |
| Wallpaper library | ⏳ Planned |
| Configuration interface | ⏳ Planned |
| Multi-monitor support | ⏳ Planned |
| Public release | ⏳ Not available yet |

*I'll update this list as development moves forward.*

## Technologies

| Component | Technology |
|:---|:---|
| Language | C++17 |
| Graphics | Direct3D 11 |
| Desktop composition | DirectComposition |
| Video playback | Media Foundation |
| Platform | Windows |

## Project files

These are the main files I'll be working on for V4.1.

| File | What it handles |
|:---|:---|
| `media_decoder.cpp` | Video playback, looping and scaling |
| `media_decoder.h` | Decoder definitions and rendering data |
| `engine_v4.cpp` | Engine and desktop integration |
| `wallpaper_config.*` | Wallpaper settings |

## Latest update

**October 31, 2026**

V4 is functional, compiled successfully and tested after the removal of temporary diagnostics.

A new backup named `v4_stable_20261031` has been created. It contains 34 copied files, with the 7 essential project files checked against the originals for matching size and timestamp.

Development is now moving towards the next phase: V4.1.

## Current status

- **Engine:** V4 functional
- **Next milestone:** V4.1
- **Platform:** Windows
- **Development:** In progress
- **Public release:** Not available yet

This repository is for presenting the project and tracking its progress. The application's source code and a public build aren't available here at the moment.

---

# Français

## À propos

Aevora est un projet de logiciel de fonds d'écran animés pour Windows sur lequel je travaille.

Je développe le moteur en C++ avec les technologies natives de Windows pour la lecture vidéo et l'intégration au bureau.

Le moteur V4 fonctionne. Il a été testé, les diagnostics temporaires ont été retirés et une nouvelle sauvegarde a été créée avant de passer à V4.1.

Le projet est toujours en développement et aucune version publique n'est disponible pour le moment.

## Avancement

### V4 — Moteur

<img src="https://img.shields.io/badge/État-Fonctionnel-2ea44f?style=for-the-badge" alt="V4 fonctionnel" />

Le moteur principal fonctionne et a été testé.

| Fonctionnalité | État |
|:---|:---:|
| Lecture vidéo MP4 / H.264 | ✅ |
| Décodage matériel si disponible | ✅ |
| Gestion des formats vidéo et solutions de secours | ✅ |
| Lecture vidéo en boucle | ✅ |
| Plus de 10 cycles consécutifs testés | ✅ |
| Arrêt propre avec `--stop` | ✅ |
| Protection contre les instances multiples | ✅ |
| Intégration au bureau Windows | ✅ |
| Récupération après redémarrage d'Explorer | ✅ |
| Gestion du verrouillage et du déverrouillage de session | ✅ |
| Gestion des changements de résolution | ✅ |
| Vérifications toutes les 5 secondes | ✅ |
| Retrait des diagnostics temporaires | ✅ |
| Recompilation réussie après nettoyage | ✅ |
| Nouvelle sauvegarde créée et contrôlée | ✅ |

<details>
<summary><strong>Problèmes connus</strong></summary>

Voici les problèmes que j'ai identifiés et qui restent à corriger ou à améliorer.

- [ ] Corriger le compteur de tentatives de lecture en boucle, qui se réinitialise actuellement et peut toujours afficher tentative 1/3.
- [ ] Implémenter correctement les modes Fit et Stretch. Le rendu actuel se comporte comme Fill.
- [ ] Examiner les deux références au périphérique D3D11 restantes à l'arrêt.
- [ ] Ajouter la détection des keyframes si une recherche vidéo précise devient nécessaire.
- [ ] Améliorer la détection des outils Visual Studio Build Tools pour éviter un chemin codé en dur.

</details>

---

## Feuille de route

### V4.1 — La suite

Voici ce que je prévois de faire ensuite.

<details open>
<summary><strong>01 — Améliorations du moteur</strong></summary>

- [ ] Corriger le compteur de tentatives.
- [ ] Implémenter correctement Fit, Fill et Stretch.
- [ ] Nettoyer les références D3D11 restantes.

</details>

<details open>
<summary><strong>02 — Bibliothèque de fonds d'écran</strong></summary>

- [ ] Scanner un dossier local pour trouver des vidéos.
- [ ] Permettre de changer de fond d'écran.
- [ ] Ajouter la gestion des playlists locales.
- [ ] Explorer les contenus Steam Workshop disponibles localement, sans intégrer l'API Steamworks dans cette phase.

</details>

<details open>
<summary><strong>03 — Paramètres</strong></summary>

- [ ] Ajouter une interface de configuration simple.
- [ ] Choisir un fond d'écran.
- [ ] Changer le mode d'affichage.
- [ ] Activer ou désactiver la lecture en boucle.
- [ ] Régler le volume.

</details>

<details>
<summary><strong>04 — Autres améliorations</strong></summary>

- [ ] Ajouter plusieurs niveaux de logs et une rotation automatique.
- [ ] Ajouter la prise en charge optionnelle des écrans secondaires.
- [ ] Tester les nouvelles fonctionnalités.

</details>

---

## Suivi de l'avancement

| Étape | État |
|:---|:---|
| Moteur V4 | ✅ Fonctionnel |
| Lecture vidéo et boucle | ✅ Testées |
| Intégration au bureau | ✅ Implémentée |
| Nettoyage des diagnostics | ✅ Terminé |
| Recompilation réussie | ✅ Vérifiée |
| Nouvelle sauvegarde | ✅ Créée et contrôlée |
| Améliorations V4.1 | 🔄 Prévues |
| Bibliothèque de fonds d'écran | ⏳ Prévue |
| Interface de configuration | ⏳ Prévue |
| Multi-écrans | ⏳ Prévu |
| Version publique | ⏳ Pas encore disponible |

*Je mettrai cette liste à jour au fur et à mesure de l'avancement.*

## Technologies

| Composant | Technologie |
|:---|:---|
| Langage | C++17 |
| Graphismes | Direct3D 11 |
| Composition du bureau | DirectComposition |
| Lecture vidéo | Media Foundation |
| Plateforme | Windows |

## Fichiers principaux

Voici les principaux fichiers sur lesquels je travaillerai pour V4.1.

| Fichier | Rôle |
|:---|:---|
| `media_decoder.cpp` | Lecture vidéo, boucle et affichage |
| `media_decoder.h` | Définitions du décodeur et données de rendu |
| `engine_v4.cpp` | Moteur et intégration au bureau |
| `wallpaper_config.*` | Paramètres des fonds d'écran |

## Dernière mise à jour

**31 octobre 2026**

Le moteur V4 fonctionne, a été recompilé avec succès et testé après le retrait des diagnostics temporaires.

Une nouvelle sauvegarde nommée `v4_stable_20261031` a été créée. Elle contient 34 fichiers copiés, dont les 7 fichiers essentiels ont été comparés aux originaux pour vérifier leur taille et leur horodatage.

Le développement se dirige maintenant vers la prochaine phase : V4.1.

## État actuel

- **Moteur :** V4 fonctionnel
- **Prochaine étape :** V4.1
- **Plateforme :** Windows
- **Développement :** En cours
- **Version publique :** Pas encore disponible

Ce dépôt sert à présenter le projet et à suivre son avancement. Le code source de l'application et une version publique ne sont pas disponibles ici pour le moment.

---

<div align="center">

**Aevora** · Projet en développement

</div>
