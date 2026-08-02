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
│   └── favicon-*.png
└── README.md
```

## Ce qui se modifie (tout est en haut du `<script>`)

### 1. Contact des candidatures — `CONTACT`

```js
const CONTACT = {
  mail : 'dagbokady@gmail.com',   // adresse qui reçoit les candidatures
  wa   : '',                       // n° WhatsApp international, ex. '2250700000000'
  objet: 'Candidature — Commission A-LEX'
};
```

Tant que `wa` est vide, le bouton WhatsApp n'est **pas affiché**. Les boutons
« Je candidate » ouvrent un e-mail pré-rempli (poste, commission, champs à remplir).

### 2. Le Bureau — `DIRECTION` et `COMMISSIONS`

`DIRECTION` = la chaîne hiérarchique de l'organigramme (Président → Vice-Président
→ Secrétaire Général). `COMMISSIONS` = les pôles affichés en dessous :

```js
{ id:'digital',                        // identifiant utilisé par les annonces
  nom:'Digital &amp; Communication',
  mission:'…',
  equipe:[ {fonction:'Responsable', nom:'DAGBO Christ-Phanuel'},
           {fonction:'Vice-Responsable', nom:'KANON Prince Elihu'} ] }
```

L'organigramme, la liste des membres et les statistiques du hero se recalculent
automatiquement à partir de ces deux tableaux.

### 3. Les annonces de recrutement — `OFFRES`

```js
{ commission:'digital',        // doit correspondre à un `id` de COMMISSIONS
  titre:'Développeur web',
  places:2,                    // nombre de postes (affiché en badge)
  ouvert:true,                 // false → annonce grisée « Candidatures closes »
  echeance:'Candidatures ouvertes',
  desc:'…',                    // 1–2 phrases
  profil:['…','…','…'] }       // puces « Profil recherché »
```

Pour **fermer** une annonce : `ouvert:false`. Pour la retirer : supprimer l'entrée.

## Résultat des élections (mandat en cours)

| Fonction | Élu(e) |
|---|---|
| Président | OUATTARA Nassir |
| Vice-Président | TAPÉ Jo Marcel |
| Secrétaire Général | DROH Michael Charles |
| Trésorier Général | KONÉ Adams Ange |
| Trésorier Adjoint | ATEBY Yannick |
| Resp. Digital & Communication | DAGBO Christ-Phanuel |
| Vice-Resp. Digital | KANON Prince Elihu |
| Resp. Mentorat & Carrière | AMA Érica |
| Vice-Resp. Mentorat & Carrière | KONÉ Isaac Hérèdè |
| Resp. Événements & Vie associative | DOUATI Dylane |
| Vice-Resp. Événements | KOUAMÉ Melvyne |
| Resp. Contrôle fiscal & administratif | KOFFI Lyvan |

## Parti pris graphique

Filets fins plutôt que pilules colorées, coins contenus (12 px cartes / 4 px puces),
l'or en accent unique, alternance de bandes navy et papier. Ce système est documenté
dans le skill Claude **`alex-brand`** (`~/.claude/skills/alex-brand/`).

---

*Association des Anciens Élèves du LEAO — Rigueur · Discipline · Excellence · Fraternité · Solidarité.*
