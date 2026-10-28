 <div align="center">

# A E V O R A

### Animated wallpapers. A more personal desktop.

A native animated wallpaper project for Windows.

<br>

![Windows](https://img.shields.io/badge/PLATFORM-WINDOWS-1684D8?style=for-the-badge&logo=windows&logoColor=white)
![Engine V4](https://img.shields.io/badge/ENGINE-V4%20FUNCTIONAL-27864B?style=for-the-badge)
![Development](https://img.shields.io/badge/NEXT-V4.1-7657D5?style=for-the-badge)
![Release](https://img.shields.io/badge/PUBLIC%20RELEASE-NOT%20AVAILABLE-555555?style=for-the-badge)

<br>

[About](#about) · [Development](#development) · [Roadmap](#roadmap) · [Technical details](#technical-details) · [Français](#français)

</div>

---

## About

Aevora is an independent project exploring animated wallpapers through a native Windows application.

The idea is simple: make the desktop feel more alive, without turning the experience into something complicated.

The project is built around a dedicated video engine and native Windows technologies. Its first major milestone, **V4, is functional**. The next phase focuses on improving reliability, adding configuration options, and building the foundations of a wallpaper library.

> Aevora is currently under development. A public release is not available yet.

## Project overview

<div align="center">

| Current milestone | Next phase | Public release |
|:---:|:---:|:---:|
| **V4** | **V4.1** | **Not available** |
| <img src="https://img.shields.io/badge/CORE-FUNCTIONAL-27864B?style=flat-square" alt="Core functional" /> | <img src="https://img.shields.io/badge/IMPROVEMENTS-PLANNED-7657D5?style=flat-square" alt="Improvements planned" /> | <img src="https://img.shields.io/badge/STATUS-IN%20DEVELOPMENT-777777?style=flat-square" alt="In development" /> |

</div>

### What Aevora is being built around

- **Native Windows integration** — designed to display animated content on the desktop.
- **Video playback** — an engine built around Media Foundation and Direct3D 11.
- **Reliability** — handling desktop changes and recovering from common interruptions.
- **Personalisation** — future controls for video selection, scaling, looping and volume.
- **Local content** — a planned library for managing wallpapers stored on the computer.

---

## Development

<div align="center">

### V4 — Core engine

<img src="https://img.shields.io/badge/STATUS-FUNCTIONAL-27864B?style=for-the-badge" alt="V4 functional" />

The initial engine requirements have been met. V4 has been compiled, tested and backed up.

</div>

### Implemented and tested

| Capability | Status |
|---|:---:|
| MP4 / H.264 video playback | ✅ |
| Media Foundation decoding pipeline | ✅ |
| Hardware decoding when available | ✅ |
| Pixel format negotiation and fallback handling | ✅ |
| Automatic video looping | ✅ |
| More than 10 consecutive loop cycles tested | ✅ |
| Clean shutdown through `--stop` | ✅ |
| Single-instance protection | ✅ |
| Attachment to the Windows desktop | ✅ |
| Recovery after Windows Explorer restarts | ✅ |
| Session lock and unlock handling | ✅ |
| Display resolution change handling | ✅ |
| Periodic health checks and automatic recovery | ✅ |
| Verified stable backup | ✅ |

<details>
<summary><strong>Engine details and known limitations</strong></summary>

#### Video pipeline

- Media Foundation Source Resolver, Media Source and Source Reader.
- Video Processor MFT enabled for video processing.
- DXVA2 / D3D11 hardware decoding when available.
- RGB32 output negotiation and fallback handling for packed pixel formats.

#### Playback and desktop integration

- The video reader is recreated at the end of the video because seeking is unsupported with the current Video Processor MFT configuration.
- The desktop attachment uses the Windows desktop window hierarchy.
- Explorer restart recovery uses the `TaskbarCreated` notification and a reattachment procedure.
- Display changes trigger swap-chain and DirectComposition target reconstruction.
- Health checks run every five seconds.

#### Remaining limitations

- [ ] **Loop retry counter:** `m_loopRetries` is reset inside `RecreateReader()`, so the log can repeatedly report attempt 1/3.
- [ ] **Scaling modes:** the current rendering stretches the texture, effectively behaving as Fill. Fit and Stretch need their intended rendering behavior implemented.
- [ ] **D3D11 cleanup:** two device references remain at shutdown. Their exact ownership still needs investigation.
- [ ] **Keyframe detection:** `isKeyFrame` is currently always false. This is only needed if precise seeking becomes a requirement.
- [ ] **Build tools discovery:** `vcvarsall.bat` is currently found through a hard-coded path because `vswhere.exe` is unavailable.

These limitations are documented for future work and do not change the current V4 milestone.

</details>

---

## Roadmap

<div align="center">

### V4.1 — The next development phase

Improvements to the engine, followed by the foundations of a configurable application.

</div>

### 01 — Playback reliability

**Status:** Planned

- [ ] Correct the loop retry counter.
- [ ] Review recovery behavior and logging.

### 02 — Scaling and rendering

**Status:** Planned

- [ ] Implement the intended Fit behavior.
- [ ] Implement the intended Stretch behavior.
- [ ] Keep Fill as the fill-the-screen option.

### 03 — Wallpaper library

**Status:** Planned

- [ ] Scan a local folder for video files.
- [ ] Support selecting between multiple wallpapers.
- [ ] Lay the groundwork for local playlists.
- [ ] Explore local Steam Workshop content where accessible, without a Steamworks API integration in this phase.

### 04 — Configuration interface

**Status:** Planned

- [ ] Select a wallpaper.
- [ ] Choose the scaling mode.
- [ ] Enable or disable looping.
- [ ] Configure volume.

### 05 — Logging

**Status:** Planned

- [ ] Add log levels.
- [ ] Implement automatic log rotation.
- [ ] Improve diagnostic messages.

### 06 — Multiple monitors

**Status:** Planned

- [ ] Keep the primary monitor as the default.
- [ ] Add optional support for secondary monitors.

### 07 — Resource cleanup

**Status:** Planned

- [ ] Investigate the remaining D3D11 references.
- [ ] Improve resource release during shutdown.

---

## Milestone tracker

This checklist is intended to evolve with the project. Completed items should reflect work that has actually been implemented and verified.

| Milestone | Progress |
|---|---|
| V4 core engine | `COMPLETE` |
| Video playback and looping | `COMPLETE` |
| Desktop integration and recovery | `COMPLETE` |
| Stable backup | `VERIFIED` |
| V4.1 reliability improvements | `PLANNED` |
| Rendering and scaling improvements | `PLANNED` |
| Wallpaper library and configuration UI | `PLANNED` |
| Multi-monitor support | `PLANNED` |
| Public release | `NOT AVAILABLE` |

<details>
<summary><strong>Release preparation checklist</strong></summary>

- [ ] Complete and verify the V4.1 improvements.
- [ ] Test different desktop and display configurations.
- [ ] Finalise application configuration and error handling.
- [ ] Prepare a distributable build.
- [ ] Publish release information.

</details>

---

## Technical details

<div align="center">

| Component | Technology |
|:---|:---|
| Language | C++17 |
| Graphics | Direct3D 11 |
| Desktop composition | DirectComposition |
| Video playback | Media Foundation |
| Platform | Windows |

</div>

### Project structure

The following files are key areas of the current development work.

| File | Responsibility |
|---|---|
| `media_decoder.cpp` | Video decoding, looping and scaling |
| `media_decoder.h` | Decoder definitions and rendering-related data |
| `engine_v4.cpp` | Engine lifecycle, desktop integration and future application features |
| `wallpaper_config.*` | Wallpaper configuration and future settings |

### Development environment

The current engine is developed and built on Windows. The V4 working directory and its stable backup are maintained separately.

The application source code and a public distributable are **not provided through this presentation repository**.

---

## Latest update

<div align="center">

**28 October 2026**

### V4 milestone reached

</div>

The V4 engine has been compiled and tested against its initial requirements. A stable backup has also been verified, with 32 files matching the source byte for byte.

Development is now ready to move toward V4.1, beginning with smaller reliability and rendering improvements before expanding the application.

---

## Project status at a glance

<div align="center">

| | |
|:---|:---|
| **Project** | Aevora |
| **Category** | Animated wallpaper software |
| **Platform** | Windows |
| **Engine** | V4 — functional |
| **Next milestone** | V4.1 |
| **Development** | In progress |
| **Public build** | Not available |

</div>

---

# Français

## À propos

Aevora est un projet de logiciel de fonds d'écran animés développé nativement pour Windows.

L'idée est simple : rendre le bureau plus vivant, sans compliquer son utilisation.

Le projet s'appuie sur un moteur vidéo dédié et sur les technologies natives de Windows. Le moteur V4 a atteint son premier jalon fonctionnel. La prochaine phase vise à améliorer sa fiabilité, à ajouter des options de configuration et à poser les bases d'une bibliothèque de fonds d'écran.

> Aevora est toujours en développement. Aucune version publique n'est disponible pour le moment.

## Vue d'ensemble

<div align="center">

| Jalon actuel | Prochaine phase | Version publique |
|:---:|:---:|:---:|
| **V4** | **V4.1** | **Non disponible** |
| <img src="https://img.shields.io/badge/COEUR-FONCTIONNEL-27864B?style=flat-square" alt="Cœur fonctionnel" /> | <img src="https://img.shields.io/badge/AMÉLIORATIONS-PRÉVUES-7657D5?style=flat-square" alt="Améliorations prévues" /> | <img src="https://img.shields.io/badge/ÉTAT-EN%20DÉVELOPPEMENT-777777?style=flat-square" alt="En développement" /> |

</div>

### Les objectifs d'Aevora

- **Intégration native à Windows** — afficher des contenus animés sur le bureau.
- **Lecture vidéo** — un moteur basé sur Media Foundation et Direct3D 11.
- **Fiabilité** — gérer les changements du bureau et récupérer après certaines interruptions.
- **Personnalisation** — ajouter des réglages pour la vidéo, l'affichage, la boucle et le volume.
- **Contenus locaux** — créer une bibliothèque de fonds d'écran stockés sur l'ordinateur.

---

## Développement

<div align="center">

### V4 — Moteur principal

<img src="https://img.shields.io/badge/ÉTAT-FONCTIONNEL-27864B?style=for-the-badge" alt="V4 fonctionnel" />

Les exigences initiales du moteur sont satisfaites. La V4 a été compilée, testée et sauvegardée.

</div>

### Fonctionnalités implémentées et testées

| Fonctionnalité | État |
|---|:---:|
| Lecture vidéo MP4 / H.264 | ✅ |
| Pipeline de décodage Media Foundation | ✅ |
| Décodage matériel si disponible | ✅ |
| Négociation des formats et buffers de secours | ✅ |
| Lecture vidéo en boucle | ✅ |
| Plus de 10 cycles consécutifs testés | ✅ |
| Arrêt propre avec `--stop` | ✅ |
| Protection contre les instances multiples | ✅ |
| Attache au bureau Windows | ✅ |
| Récupération après redémarrage d'Explorer | ✅ |
| Gestion du verrouillage et déverrouillage de session | ✅ |
| Gestion des changements de résolution | ✅ |
| Vérifications périodiques et récupération automatique | ✅ |
| Sauvegarde stable vérifiée | ✅ |

<details>
<summary><strong>Détails techniques et limitations connues</strong></summary>

#### Pipeline vidéo

- Media Foundation Source Resolver, Media Source et Source Reader.
- Video Processor MFT activé pour le traitement vidéo.
- Décodage matériel DXVA2 / D3D11 lorsqu'il est disponible.
- Négociation de sortie RGB32 et gestion de secours pour les formats de pixels packés.

#### Lecture et intégration au bureau

- Le lecteur vidéo est recréé à la fin de la vidéo, car la recherche temporelle n'est pas prise en charge avec la configuration actuelle du Video Processor MFT.
- L'attache au bureau repose sur la hiérarchie des fenêtres du bureau Windows.
- La récupération après un redémarrage d'Explorer utilise la notification `TaskbarCreated`.
- Les changements d'affichage déclenchent la reconstruction de la swap chain et de la cible DirectComposition.
- Les vérifications de santé sont effectuées toutes les cinq secondes.

#### Limitations restantes

- [ ] **Compteur de tentatives :** `m_loopRetries` est remis à zéro dans `RecreateReader()`, ce qui peut répéter le message tentative 1/3.
- [ ] **Modes d'affichage :** le rendu actuel étire la texture, ce qui correspond au comportement Fill. Fit et Stretch doivent encore être implémentés correctement.
- [ ] **Nettoyage D3D11 :** deux références au périphérique subsistent à l'arrêt. Leur origine exacte reste à examiner.
- [ ] **Détection des keyframes :** `isKeyFrame` vaut actuellement toujours false. Cette fonction ne sera nécessaire que si une recherche précise devient indispensable.
- [ ] **Détection des outils de compilation :** `vcvarsall.bat` est actuellement trouvé via un chemin codé en dur, car `vswhere.exe` est absent.

Ces limitations sont documentées pour les prochaines étapes et ne remettent pas en cause le jalon fonctionnel de V4.

</details>

---

## Feuille de route

<div align="center">

### V4.1 — La prochaine phase

Améliorer le moteur, puis poser les bases d'une application configurable.

</div>

### 01 — Fiabilité de la lecture

**État :** Prévu

- [ ] Corriger le compteur de tentatives de lecture en boucle.
- [ ] Examiner la récupération et les journaux.

### 02 — Affichage et rendu

**État :** Prévu

- [ ] Implémenter le comportement Fit.
- [ ] Implémenter le comportement Stretch.
- [ ] Conserver Fill comme option de remplissage de l'écran.

### 03 — Bibliothèque de fonds d'écran

**État :** Prévu

- [ ] Scanner un dossier local contenant des vidéos.
- [ ] Permettre de choisir entre plusieurs fonds d'écran.
- [ ] Préparer la gestion de playlists locales.
- [ ] Explorer les contenus Steam Workshop accessibles localement, sans intégration à l'API Steamworks dans cette phase.

### 04 — Interface de configuration

**État :** Prévu

- [ ] Sélectionner un fond d'écran.
- [ ] Choisir le mode d'affichage.
- [ ] Activer ou désactiver la boucle.
- [ ] Régler le volume.

### 05 — Journalisation

**État :** Prévu

- [ ] Ajouter des niveaux de logs.
- [ ] Mettre en place la rotation automatique des journaux.
- [ ] Améliorer les messages de diagnostic.

### 06 — Multi-écrans

**État :** Prévu

- [ ] Conserver l'écran principal comme choix par défaut.
- [ ] Ajouter la prise en charge optionnelle des écrans secondaires.

### 07 — Nettoyage des ressources

**État :** Prévu

- [ ] Examiner les références D3D11 restantes.
- [ ] Améliorer la libération des ressources à l'arrêt.

---

## Suivi des jalons

Cette liste doit évoluer avec le projet. Une tâche ne doit être cochée qu'une fois son implémentation vérifiée.

| Jalon | Avancement |
|---|---|
| Moteur principal V4 | `TERMINÉ` |
| Lecture vidéo et boucle | `TERMINÉ` |
| Intégration au bureau et récupération | `TERMINÉ` |
| Sauvegarde stable | `VÉRIFIÉE` |
| Améliorations de fiabilité V4.1 | `PRÉVU` |
| Améliorations du rendu et de l'affichage | `PRÉVU` |
| Bibliothèque et interface de configuration | `PRÉVU` |
| Prise en charge multi-écrans | `PRÉVU` |
| Version publique | `NON DISPONIBLE` |

<details>
<summary><strong>Liste de préparation de la sortie</strong></summary>

- [ ] Terminer et vérifier les améliorations V4.1.
- [ ] Tester différentes configurations de bureau et d'affichage.
- [ ] Finaliser la configuration et la gestion des erreurs.
- [ ] Préparer une version distribuable.
- [ ] Publier les informations sur la sortie.

</details>

---

## Détails techniques

<div align="center">

| Composant | Technologie |
|:---|:---|
| Langage | C++17 |
| Graphismes | Direct3D 11 |
| Composition du bureau | DirectComposition |
| Lecture vidéo | Media Foundation |
| Plateforme | Windows |

</div>

### Fichiers principaux

| Fichier | Rôle |
|---|---|
| `media_decoder.cpp` | Décodage vidéo, boucle et affichage |
| `media_decoder.h` | Définitions du décodeur et données liées au rendu |
| `engine_v4.cpp` | Cycle de vie du moteur, intégration au bureau et futures fonctionnalités |
| `wallpaper_config.*` | Configuration des fonds d'écran et futurs réglages |

### Environnement de développement

Le moteur actuel est développé et compilé sous Windows. Le répertoire de travail V4 et sa sauvegarde stable sont conservés séparément.

Le code source de l'application et une version distribuable publique ne sont **pas fournis dans ce dépôt de présentation**.

---

## Dernière mise à jour

<div align="center">

**28 octobre 2026**

### Premier jalon V4 atteint

</div>

Le moteur V4 a été compilé et testé selon les exigences initiales. Une sauvegarde stable a également été vérifiée : les 32 fichiers correspondent octet par octet à la source.

Le développement peut maintenant passer à V4.1, en commençant par les améliorations de fiabilité et de rendu avant d'élargir les possibilités de l'application.

---

## État du projet en bref

<div align="center">

| | |
|:---|:---|
| **Projet** | Aevora |
| **Catégorie** | Logiciel de fonds d'écran animés |
| **Plateforme** | Windows |
| **Moteur** | V4 — fonctionnel |
| **Prochain jalon** | V4.1 |
| **Développement** | En cours |
| **Version publique** | Non disponible |

</div>

---

<div align="center">

**Aevora**

*Un bureau plus vivant, une étape à la fois.*

<sub>Project in development · Projet en développement</sub>

</div>
