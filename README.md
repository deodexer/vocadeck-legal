# Vocadeck

Application mobile Android de flashcards français ↔ anglais avec répétition espacée (SRS), synchronisation cloud et interface bilingue.

---

## Présentation

Vocadeck est une application conçue pour apprendre le vocabulaire français-anglais à travers des **sessions de révision par flashcards**. Elle intègre l'algorithme de répétition espacée **SM-2** qui adapte automatiquement la fréquence de révision de chaque carte selon ta performance. L'idée : réviser uniquement ce que tu risques d'oublier, au bon moment, sans effort de planification.

**Fonctionnalités principales :**
- Création de cartes avec **traduction automatique** FR ↔ EN (API MyMemory)
- Sessions de révision avec vote de difficulté (Difficile / Normal / Facile)
- Algorithme SRS SM-2 — l'intervalle de révision évolue selon tes votes
- Organisation par **catégories** avec couleurs personnalisées
- **Synthèse vocale** intégrée (TTS) pour chaque mot
- Synchronisation temps réel via **Firebase Firestore** (multi-appareils)
- Compte invité anonyme ou connexion Google
- Interface disponible en **français** et **anglais**
- Mode sombre / clair

---

## Installation

> L'application n'est pas encore publiée sur le Play Store.
> Tu peux l'installer manuellement via le fichier `.apk`.

1. Télécharge `app-release.apk` depuis la section [Releases](../../releases)
2. Sur Android : *Paramètres → Sécurité → Autoriser les sources inconnues*
3. Ouvre le fichier APK et installe

---

## Guide d'utilisation

### Écran principal

L'écran d'accueil liste toutes tes cartes, regroupées par **catégories** (blocs colorés).

| Geste | Action |
|-------|--------|
| Appui sur un bloc de catégorie | Lancer une session avec les cartes de cette catégorie |
| **Appui long sur un bloc de catégorie** | Modifier le nom ou la couleur de la catégorie |
| Appui sur une carte | Ouvrir la carte pour la modifier |
| Bouton « Session aléatoire » | Lancer une session avec toutes les cartes mélangées |
| Bouton + (bas droite) | Créer une nouvelle carte |
| Filtres Difficile / Normal / Facile | Lancer une session filtrée par niveau de difficulté |

---

### Créer une carte

1. Appuie sur **+** (bas droite de l'écran principal)
2. Tape le mot ou la phrase en **anglais** (champ du haut)
3. Appuie sur l'**icône de traduction ↔** pour traduire automatiquement vers le français
4. La traduction se place dans le champ français — modifie-la si besoin
5. **Valider avec Entrée** dans le champ anglais déplace automatiquement le curseur vers le champ français
6. Ajoute une **catégorie** (optionnel) — commence à taper pour l'auto-complétion
7. Appuie sur **Enregistrer**

> La traduction fonctionne dans les deux sens (FR→EN ou EN→FR).

---

### Session de révision

Une session affiche les cartes une par une en mode plein écran.

| Geste | Action |
|-------|--------|
| Appui sur la carte | Retourner la carte (voir la traduction) + écouter la prononciation |
| Glissement horizontal ou vertical | Passer à la carte suivante / revenir à la précédente |
| **Appui long sur la carte** | Ouvrir l'écran de modification de la carte en cours |

Après avoir retourné la carte, trois boutons apparaissent :

- **Difficile** — la carte sera représentée très bientôt (intervalle court)
- **Normal** — intervalle modéré
- **Facile** — long intervalle avant la prochaine révision

> L'icône 🔇 en haut à droite coupe la synthèse vocale.  
> À la fin du paquet, les cartes sont automatiquement remélangées pour un nouveau tour.

---

### Modifier une carte

- Depuis l'écran principal : **appuie sur la carte**
- Depuis une session : **appui long** sur la carte

Dans l'écran de modification :
- Modifie le texte, la catégorie, le niveau de difficulté
- **Appuyer sur le chip de difficulté actif** le désactive (remet la carte en "non notée")
- **Icône poubelle** (haut droite) → supprimer la carte définitivement

---

### Menu hamburger (≡)

Accessible depuis l'écran principal via l'icône en haut à gauche.

| Option | Description |
|--------|-------------|
| Changer la langue | Basculer l'interface FR / EN |
| Confidentialité | Politique de confidentialité |
| Signaler un bug | Formulaire de rapport (requiert un compte Google) |
| Notes de version | Historique des mises à jour |
| Se déconnecter | Synchronise les données puis déconnecte |
| Vider toutes les données | Supprime toutes les cartes et catégories |
| Supprimer mon compte | Suppression RGPD complète (données + compte) |

---

### Compte et synchronisation

- Au premier lancement : un **compte invité anonyme** est créé automatiquement (aucun compte requis)
- Pour synchroniser sur plusieurs appareils : **Lier avec Google** dans le menu hamburger
- Le badge nuage (☁) en haut du menu indique l'état de la synchronisation (en cours / synchronisé / erreur)
- Les données locales sont automatiquement poussées vers le cloud avant déconnexion

---

## Architecture technique

| Couche | Technologie |
|--------|-------------|
| UI | Flutter / Material 3 |
| État | Riverpod |
| Base locale | Drift (SQLite) |
| Cloud | Firebase Firestore + Firebase Auth |
| SRS | Algorithme SM-2 |
| Traduction | MyMemory API (gratuit, sans clé) |

---

## Changelog

Voir [CHANGELOG.md](CHANGELOG.md) pour l'historique des versions.

---

## Licence

Projet personnel — tous droits réservés.
