# patrimoine-visuels

Dépôt d'archivage des visuels hebdomadaires (posts LinkedIn/Instagram) pour
un cabinet de gestion de patrimoine (contenu en français).

## Contenu du dépôt

Uniquement des PNG finaux, nommés `2026-S{semaine}-{n}-{hash4}.png`
(`{n}` = numéro du post publié cette semaine-là, identique pour toutes
les slides d'un même post ; `{hash4}` = 4 caractères hex, un par slide).
Aucune source (HTML, script) n'est committée — seul le rendu final.

## Objectif de chaque post : donner envie de s'abonner et de prendre RDV

Un post n'est pas qu'informatif. Le but final est toujours que le lecteur
ait envie (a) de s'abonner et (b) de prendre rendez-vous avec Karine. Un
post qui n'arrête pas le scroll ne convertit jamais — donc **l'accroche
(titre du visuel ET première ligne de la légende) doit toujours être
optimisée pour la performance**, jamais juste "correcte". Se challenger
systématiquement, ne pas valider la première version venue.

Techniques à mobiliser pour l'accroche (utiliser au moins une, idéalement
en combiner deux) :

- **Question directe qui force une auto-évaluation** ("Vous connaissez
  votre TMI ?") plutôt qu'une affirmation plate — crée une micro-décision
  (je sais / je ne sais pas) qui engage avant même la réponse.
- **Remise en cause d'une croyance commune** ("X n'est pas Y.") — crée
  une tension à résoudre, pousse à lire la suite pour comprendre.
- **Chiffre concret et spécifique** plutôt que vague ("11 500 €" plutôt
  que "beaucoup d'argent") — la précision rend crédible et arrête le
  scroll.
- **Enjeu personnel immédiat** : le lecteur doit sentir que ça le
  concerne lui, maintenant, pas "les gens" en général.

**Jamais une accroche purement déclarative/informative** ("X permet de
Y.", "Voici les priorités selon Z.") — ça se lit passivement et n'arrête
pas le pouce. Toujours une tension, une question, ou un contraste.

Pour la légende : terminer le corps du post (avant la signature) par une
question ouverte qui invite à l'échange, jamais commerciale. Avant de
valider un post, se demander : "si je ne connaissais pas Karine, cette
accroche me donnerait-elle envie de lire la suite, et ce post me
donnerait-il envie de prendre RDV ?" Si non, retravailler l'accroche
avant de générer le visuel.

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
- **Grille de référence / auto-évaluation (1 visuel dense)** : le format
  qui performe le mieux chez les consœurs/confrères du secteur (ex.
  Pauline Gonzales) n'est pas la punchline mais l'**outil dans lequel le
  lecteur se cherche** — barème "combien devriez-vous avoir de côté selon
  vos revenus", grille d'auto-évaluation avec scoring ("8-10 points :
  vous maîtrisez..."), tableau comparatif chiffré (cash vs crédit, droits
  de succession selon montant/nombre d'enfants), schéma de répartition
  patrimoniale. Le ressort psychologique : donner un repère concret pour
  que chacun se situe, pas juste une affirmation à lire passivement.
  Adapté quand le sujet a une dimension quantitative/personnelle
  ("où j'en suis par rapport à la moyenne, à ce que je devrais avoir").

**Important : s'inspirer du mécanisme, jamais du contenu ni du visuel
d'un post déjà publié par quelqu'un d'autre.** Reprendre l'idée générale
(un barème, une grille de score, un tableau croisé) est légitime ; copier
les mêmes chiffres, le même tableau ou la charte graphique d'un autre
cabinet (rouge/beige façon papier pour Pauline Gonzales, par exemple) ne
l'est pas — toujours un sujet et des chiffres différents, toujours dans
la charte graphique de Karine (voir plus bas).

Si le carrousel est retenu, ajouter dans la légende une invitation à
swiper après l'accroche (ex. "(swipe pour comprendre pourquoi ➡️)").

**Carrousel → toujours fournir aussi un PDF.** LinkedIn n'affiche un
carrousel swipeable que via un post "document" (PDF, PPT ou DOC) — importer
plusieurs images séparées ne donne pas un carrousel sur LinkedIn (contrairement
à Instagram). Donc pour tout post en carrousel : générer un PDF multi-pages
(une slide = une page, même ordre que les PNG) à partir des PNG déjà rendus
(`PIL: im1.save(path, save_all=True, append_images=[im2, ...])`), le committer
dans le dépôt avec le même nom que les slides (`2026-S{semaine}-{n}-{hash4}.pdf`),
et l'envoyer à l'utilisatrice avec les PNG.

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
- **Lisibilité et densité — erreur récurrente à ne pas reproduire** : sur
  mobile, un visuel affiché en miniature avec du texte trop petit ou trop
  d'espace mort se lit mal et perd en impact. Toujours composer pour que
  le contenu occupe l'espace utile du carré (entre les équerres, environ
  y=140 à y=1060) plutôt que de laisser un tiers du bas vide. Tailles
  minimales à respecter (Poppins/Nunito, canvas 1200x1200) : titre
  principal ≥ 48px, corps/sous-titre ≥ 26px, libellé de détail dans une
  carte ≥ 22px, rien en dessous de 20px nulle part. Pour une liste de
  items (checklist, grille de référence), dimensionner les cartes pour
  qu'elles remplissent la hauteur disponible plutôt que de garder des
  cartes compactes avec du vide en dessous — quitte à réduire le nombre
  d'items si le sujet ne justifie pas de les agrandir davantage.
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

**Format de livraison par défaut : un bloc de code dans le message de
chat** (fence markdown triple-backtick), pas un fichier .txt envoyé en
pièce jointe — sur mobile, le bloc de code a un bouton "copier" en un tap,
plus pratique qu'un fichier à ouvrir/télécharger. Ne pas committer ce
texte dans le dépôt (qui n'archive que les visuels).

### Signature (à ajouter systématiquement en fin de légende, tous posts)

Toujours ajouter ce bloc, verbatim, à la toute fin de la légende (après le
CTA propre au post et l'éventuel disclaimer de simulation), séparé par une
ligne vide :

```
Enchantée, moi c'est Karine.
🤝 J'aide les gens à investir avec une stratégie claire et adaptée.
🌱 J'accompagne aussi celles et ceux qui souhaitent se lancer dans le conseil financier.
📅 Une question sur ta situation ? Le bouton "Prendre un rendez-vous" est juste au-dessus
```

Note : cette signature est au tutoiement ("ta situation") alors que le
corps du post est généralement au vouvoiement — c'est volontaire (choix de
Karine), ne pas essayer d'harmoniser le registre.

## Cadence

Publication **2 fois par semaine, tous les mardis et jeudis matin** — ce
n'est pas exceptionnel, c'est le rythme normal. `{n}` dans le nom de
fichier est le numéro chronologique du post dans la semaine (1 = premier
post publié, généralement le mardi ; 2 = le second, généralement le
jeudi). Toujours vérifier le numéro de semaine ISO réel avant de nommer
le fichier (`date +%V`), ne pas se fier au dernier post committé si
plusieurs semaines ou publications ont été sautées.
