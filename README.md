# A-LEX — Le Bureau Exécutif & les Commissions

Page web statique qui présente le **Bureau Exécutif d'A-LEX** issu des élections
(organigramme + membres élus) et publie les **appels à candidature** pour rejoindre
les commissions.

> Les élections sont closes : cette page ne sert plus au vote ni à la présentation
> des candidats. Les lettres de candidature restent dans l'historique Git.

« Qui cultive la Rigueur et la Discipline cueille l'Excellence »

---

## Aperçu

- **Un seul fichier** à ouvrir : [`index.html`](index.html) (HTML + CSS + JS).
- **Identité reprise du nouveau logo A-LEX** (BrandBoard) :
  Navy `#0B2240` · Navy profond `#031E35` · Or `#D4AF37` · Or foncé `#A37F33` ·
  Or clair `#E8C86C` · Papier `#F4F4F6` / `#E9E9EB`.
- **Police Montserrat** (Google Fonts, repli Helvetica/Arial hors ligne).
- **Responsive**, apparitions au défilement, compteurs, retour en haut.

## Lancer le site

```bash
python3 -m http.server 4599
```

puis ouvrir <http://localhost:4599>. (Un double-clic sur `index.html` fonctionne aussi.)

## Structure

```
votes-alex/
├── index.html               # La page (contenu, style, scripts)
├── assets/
│   ├── logo-alex.png        # Logo principal (navy) — fonds clairs
│   ├── logo-alex-blanc.png  # Logo blanc + or — fonds navy
│   ├── logo.png             # Ancien écusson (conservé)
│   └── favicon-*.png        # Monogramme « A » blanc + vague or sur navy
│                            # (32 / 48 / 180 / 192 / 512 px), généré depuis le logo
└── README.md
```

## Ce qui se modifie (tout est en haut du `<script>`)

### 1. Contact des candidatures — `CONTACT`

```js
const CONTACT = {
  wa   : '2250584904863',         // n° WhatsApp qui reçoit les candidatures
  mail : 'dagbokady@gmail.com',   // adresse de secours (bouton e-mail)
  objet: 'Candidature — Commission A-LEX'
};
```

Chaque bouton « Postuler » ouvre `wa.me/<numéro>` avec un message pré-rempli
(commission, poste, nom, promotion).

### 1 bis. Les réseaux sociaux — `SOCIAL`

```js
{ nom:'Facebook', url:'https://…', ic:'<path d="…"/>' }   // `ic` = tracé SVG 24×24
```

L'ordre du tableau est celui affiché dans la section de clôture (avec libellé) et
dans le pied de page (icônes seules).

### 2. Le Bureau — `DIRECTION` et `COMMISSIONS`

`DIRECTION` = la chaîne hiérarchique de l'organigramme (Président → Vice-Président
→ Secrétaire Général). `COMMISSIONS` = les pôles affichés en dessous :

```js
{ id:'digital',                        // identifiant utilisé par les annonces
  nom:'Digital &amp; Communication',
  mission:'…',
  equipe :[ {fonction:'Responsable', nom:'DAGBO Christ-Phanuel'},
            {fonction:'Vice-Responsable', nom:'KANON Prince'} ],
  membres:[ {nom:'KEITA Almamy'},
            {nom:'KOUAKOU Allah Yannick', promo:'A-LEX 3'} ] }  // `promo` facultatif
```

L'organigramme, la liste des membres et les statistiques du hero se recalculent
automatiquement à partir de ces deux tableaux.

### 3. Les annonces de recrutement — `OFFRES`

```js
{ commission:'digital',      // doit correspondre à un `id` de COMMISSIONS
  titre:'Montage vidéo',
  places:1,                  // facultatif — sans `places`, le badge affiche « Ouvert »
  ouvert:true,               // false → annonce grisée « Candidatures closes »
  precision:'…',             // facultatif — ex. « Dont au moins un A-LEX 4 »
  desc:'…',                  // facultatif
  profil:['…','…'] }         // facultatif — bloc « Profil recherché » masqué si absent
```

Seul `commission`, `titre` et `ouvert` sont obligatoires : **tant qu'une commission
n'a pas donné de critères, on n'en invente pas** — la carte reste volontairement nue.

Pour **fermer** une annonce : `ouvert:false`. Pour la retirer : supprimer l'entrée.

## Composition du mandat en cours

**Direction** — Président : OUATTARA Nassir · Vice-Président : TAPÉ Jo Marcel ·
Secrétaire Général : DROH Michael Charles.

| Commission | Responsable / Adjoint | Membres |
|---|---|---|
| Trésorerie | KONÉ Adams Ange / ATEBY Yannick | KOUAKOU Allah Yannick (A-LEX 3), BONI Gil-André (A-LEX 5), HOUSSOU Delphine (A-LEX 1), BROU Ange (A-LEX 2), GOLLYS Emmanuel (A-LEX 1), COULIBALY Mariam (A-LEX 3) |
| Digital & Communication | DAGBO Christ-Phanuel / KANON Prince | KEITA Almamy, DADIÉ Hanniel, NAOUA Eden, KONÉ Daouda |
| Mentorat & Carrière | AMA Érica Axelle-Nelly / KONÉ Mohamed Isaac Hérèdé | KODJO Ezoua Astrid Marie-Carmel |
| Événements & Vie associative | DOUATI Dylane / KOUAMÉ Melvyne | SANGARÉ Awa, DOKUYO, ALLA Yannick |
| Contrôle administratif | KOFFI Lyvan / ESSEHIN Emyce | — |

**Recrutements en cours** : Trésorerie 2 places (dont au moins un A-LEX 4) ·
Contrôle administratif 3 places · Digital 1 montage vidéo, 1 affiches,
2 couverture photo/vidéo · Événements et Mentorat ouverts (nombre non précisé).

## Parti pris graphique

Filets fins plutôt que pilules colorées, coins contenus (12 px cartes / 4 px puces),
l'or en accent unique, alternance de bandes navy et papier. Ce système est documenté
dans le skill Claude **`alex-brand`** (`~/.claude/skills/alex-brand/`).

---

*Association des Anciens Élèves du LEAO — Rigueur · Discipline · Excellence · Fraternité · Solidarité.*
