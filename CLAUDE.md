# Patrimoine Visuels — Karine Sevin (CGP)

Ce repo stocke les visuels de carrousels LinkedIn de Karine Sevin, Conseillère en
Gestion de Patrimoine (Biot, PACA). Contenu pédagogique patrimonial (assurance-vie,
démembrement, LEP...) + posts orientés conversion (prise de RDV via bouton Calendly
LinkedIn Premium).

## Objectif business

Prise de RDV (pas juste notoriété). CTA à privilégier : renvoyer vers le bouton
"Prendre un rendez-vous" du profil LinkedIn plutôt qu'un lien externe en post (les
liens externes pénalisent la portée). Éviter le funnel DM sauf besoin spécifique.

Cadence actuelle : mardi + jeudi, 8h30.

## Contexte réseau (à surveiller, pas à répéter comme diagnostic à chaque post)

~3200 abonnés, majoritairement issus de connexions automatisées peu qualifiées →
taux d'engagement dilué. Piste en cours : resserrer le ciblage (secteur, taille
d'entreprise, zone géo, moment de vie) plutôt que le volume, mesurer profils qui
reviennent/cliquent "Prendre RDV" plutôt que les impressions brutes.

## Identité visuelle (validée le 2026-08-04)

Référence de marque : bannière LinkedIn de Karine — dégradé violet → vert turquoise,
bloc surligneur turquoise vif façon feutre, accent corail (bandeau "Prends RDV").

**Ne pas repartir sur un thème clair/pastel générique** — testé et rejeté (jugé
"fade, insipide, perte d'identité"). L'identité doit rester le dégradé sombre
violet/turquoise en fond ; le clair sert uniquement d'encart de lisibilité à
l'intérieur, pas de fond principal.

Template de référence réutilisable : `template-carrousel-45.html` (renvoie
`2026-S32-1-identite-45-v2-4a4b.png` une fois rendu — dernière version validée).

### Specs

- **Format : 1080×1350 (ratio 4:5)**, pas de carré 1200×1200. Le carré crée du
  letterboxing (bandes noires) en plein écran mobile et dans le feed — mauvais usage
  de l'espace écran. Le 4:5 est le format à utiliser pour tous les prochains visuels.
- **Fond** : dégradé diagonal 135deg `#2B1750 → #3C2168 → #1C4A4A → #0A2E2B` +
  deux radial-gradients discrets (violet 15%/8%, turquoise 92%/90%) pour la texture.
- **Accents** : turquoise `#32E1C4` (primaire), corail `#FF7A5C` (secondaire).
- **Titre** : blanc gras, avec la phrase clé sur fond turquoise façon surligneur
  (léger `rotate(-1.1deg)`, texte marine `#12233F`), pas juste du texte coloré.
- **Brackets de coin** (top-left + bottom-right, 70×70px, bordure turquoise 5px,
  arrondi 14px) : élément de marque à garder sur tous les visuels.
- **Encart clair interne** : PAS plein cadre (a été testé plein cadre → jugé "trop
  de vide" puis "encore trop grand" une fois agrandi). Réglage validé : largeur
  ~87%, hauteur fixe ~700px, centré horizontalement ET verticalement dans l'espace
  sous le titre (pas de `flex:1` qui écrase le fond identité). Fond
  blanc → turquoise très pâle (`#EAFBF7`), coins arrondis 34px, ombre portée.
- **Répartition du contenu dans l'encart** : `justify-content: space-evenly` (pas
  `center`) pour éviter tout vide résiduel autour du bloc de texte/icône, même si
  la hauteur de l'encart change. Icônes emoji ~90px pour occuper l'espace
  (ex. 🌳 nu-propriétaire / 🍎 usufruitier) plutôt que d'agrandir les marges.
- **Cartes de comparaison 2 colonnes** : liseré haut coloré (teal / corail),
  pastille colorée pour le label, séparateur vertical fin entre les 2 colonnes.

### Pipeline de rendu (bug connu à toujours appliquer)

Chromium headless (`/opt/pw-browsers/chromium-1194/chrome-linux/chrome`) tronque
le bas du rendu d'environ 90-120px si `--window-size` correspond exactement aux
dimensions cible (bande blanche parasite invisible sur fond clair, visible sur
fond sombre). **Toujours** rendre avec une hauteur de fenêtre supérieure d'environ
120px à la cible, puis recadrer précisément à la taille finale avec Pillow.

```bash
chrome --headless --disable-gpu --no-sandbox --hide-scrollbars \
  --force-device-scale-factor=1 --window-size=1080,1470 \
  --screenshot=raw.png "file://$(pwd)/template-carrousel-45.html"
python3 -c "from PIL import Image; Image.open('raw.png').crop((0,0,1080,1350)).save('final.png')"
```

## Convention de nommage des fichiers

`2026-Sxx-<n°slide>-<tag>-<hash4>.png` — le hash est un identifiant aléatoire
(`openssl rand -hex 2`), le tag décrit la variante quand pertinent (ex. `identite`,
`clair`, `45`).
