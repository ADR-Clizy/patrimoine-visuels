# patrimoine-visuels

Dépôt d'archivage des visuels hebdomadaires (posts LinkedIn/Instagram) pour
un cabinet de gestion de patrimoine (contenu en français).

## Contenu du dépôt

Uniquement des PNG finaux, nommés `2026-S{semaine}-{n}-{hash4}.png`
(`{n}` = numéro du post publié cette semaine-là, identique pour toutes
les slides d'un même post ; `{hash4}` = 4 caractères hex, un par slide).
Aucune source (HTML, script) n'est committée — seul le rendu final.

## Choix du format : à adapter à chaque sujet, pas un défaut fixe

Il n'y a **pas de format par défaut**. À chaque nouveau post, évaluer le
sujet et proposer le format le plus adapté, en expliquant pourquoi. Deux
familles :

- **Visuel seul (1 slide)** : quand l'idée tient en une seule punchline ou
  un seul chiffre qui se suffit à lui-même, sans besoin de justification —
  citation, aphorisme, chiffre choc autonome. Ajouter une 2e slide dans ce
  cas dilue l'impact au lieu de l'augmenter.
- **Carrousel (2 slides ou plus)** : quand le sujet a une structure
  "accroche → explication" (chiffre choc puis pourquoi, ou mythe puis
  réalité), quand il y a plusieurs points/étapes à dérouler (ex. "les 5
  piliers de X"), ou quand on veut délibérément jouer sur le swipe pour la
  rétention. Slides cohérentes entre elles, même sujet du début à la fin
  (jamais deux thèmes différents dans un même carrousel).

Si le carrousel est retenu, ajouter dans la légende une invitation à
swiper après l'accroche (ex. "(swipe pour comprendre pourquoi ➡️)").

## Charte graphique (identité visuelle établie, à respecter à l'identique)

- Format : carré 1200x1200, PNG RGB (pas d'alpha).
- Fond : dégradé radial indigo foncé,
  `radial-gradient(circle at 50% 38%, #331454 0%, #2c1049 32%, #200c37 68%, #1a0a2c 100%)`.
- Cadre : 4 coins en équerre turquoise (`#3dd9c8`), traits 3px, bras 78px,
  inset 48px des bords.
- Couleur d'accent principale (titres, labels) : turquoise `#3dd9c8`.
- Couleur d'accent secondaire (emphase forte, alerte, contraste) : corail
  `#f0807c`.
- Cartes / panneaux : fond `#463559`, coins arrondis ~26px.
- Texte : blanc `#ffffff` (titres/chiffres), gris lavande `#c9c2d4` /
  `#afa6bb` (légendes secondaires).
- Polices (Google Fonts) : **Poppins** 700-900 pour titres/chiffres,
  **Nunito** 600-700 pour légendes et texte courant.
- Formats de carte déjà utilisés : citation/punchline seule, comparatif
  "ce qu'on croit / ce qui est vrai" en 2 colonnes, comparatif chiffré en
  2 cartes stat (label turquoise en haut, 2 chiffres avec soulignement
  corail, phrase de clôture en 2 lignes blanc puis corail).

## Méthode de génération

1. Construire une page HTML/CSS autonome reprenant la charte ci-dessus.
2. Rendre en PNG 1200x1200 avec Playwright + Chromium préinstallé
   (`/opt/pw-browsers/chromium`), puis convertir en RGB sans alpha.
3. Committer le PNG final avec un nom suivant la convention, pousser sur
   la branche de travail.

## Légende du post (à fournir systématiquement en plus du visuel)

Pour chaque visuel, toujours produire un **fichier .txt prêt à copier-coller**
contenant la légende du post, dans le style des posts LinkedIn qui
performent chez Pauline Gonzales (conseillère en gestion de patrimoine) :

- Accroche courte en gras au début, suivie d'un emoji flèche (👇).
- Le gras est simulé en Unicode (mathematical bold, pas de markdown `**`,
  qui ne s'affiche pas sur LinkedIn/Instagram) — les lettres accentuées
  (é, è, ç, û...) n'ont pas d'équivalent gras Unicode et restent en
  graisse normale, c'est un compromis normal et accepté.
- Phrases courtes, staccato, adresse directe au lecteur ("vous").
- Structure : accroche → contexte/contraste → 2-3 puces avec 👉 →
  insight/CTA doux à la fin (jamais commercial ou pushy).
- Une ligne finale de mention "simulation indicative" si le post contient
  un chiffre projeté (taux, simulation) — transparence obligatoire sur les
  hypothèses de calcul.

Ce fichier .txt est **envoyé à l'utilisateur** (via SendUserFile), il n'est
**pas committé** dans ce dépôt (qui n'archive que les visuels).

## Cadence

Publication le jeudi matin. Toujours vérifier le numéro de semaine ISO
réel avant de nommer le fichier (`date +%V`), ne pas se fier au dernier
post committé si plusieurs semaines ont été sautées.
