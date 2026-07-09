# A-LEX — Présentations des candidats

Page web statique qui présente, **poste par poste**, les membres de l'association
**A-LEX** (Association des Anciens Élèves du Lycée d'Excellence Alassane Ouattara
de Grand-Bassam) qui se sont désignés pour un poste, ainsi que **leur lettre de
motivation reproduite intégralement**.

> Cette page **ne sert pas au vote ni au dépôt de candidature**. Elle met en
> valeur les prises de parole des membres déjà désignés.

« Qui cultive la Rigueur et la Discipline cueille l'Excellence »

---

## Aperçu

- **Un seul fichier** à ouvrir : [`index.html`](index.html) (HTML + CSS + JS, sans dépendance externe).
- **Police** : Helvetica (Helvetica Neue → Helvetica → Arial en repli).
- **Charte graphique A-LEX** reprise du support de présentation :
  - Navy `#0D2841`, Or `#F1BA27`, Crème `#F7F2E4`.
- **Responsive** (ordinateur, tablette, mobile), animations d'apparition au défilement,
  compteurs animés, bouton « retour en haut ».
- **Page simple, sans menu** : on fait défiler la page de haut en bas.

## Lancer le site

Aucune installation n'est nécessaire.

- **Le plus simple** : double-cliquer sur `index.html` pour l'ouvrir dans un navigateur.
- **Avec un petit serveur local** (utile sur certains navigateurs) :
  ```bash
  cd Candidats
  python3 -m http.server 4599
  # puis ouvrir http://localhost:4599
  ```

## Structure du dossier

```
Candidats/
├── index.html          # La page (contenu, style et scripts)
├── assets/
│   ├── logo.png        # Écusson A-LEX (fond détouré, transparent)
│   └── favicon-*.png   # Favicon (écusson sur fond navy, plusieurs tailles)
└── README.md           # Ce fichier
```

## Postes présentés

Les postes et leurs missions/rôles proviennent du document officiel
« Rôles & missions ». Les présentations reçues sont réparties ainsi :

Noms et classes (TC1 / TC2 / TD = classe de terminale au LEAO) tels que sur le
bulletin officiel :

| Poste (bulletin)                        | Candidat(s) — classe |
|-----------------------------------------|----------------------|
| Président                               | Ouattara Ibrahim Nassir (TC1) |
| Vice-Président                          | Tapé Jo Marcel Brito (TC1) |
| Secrétaire Général                      | Droh Michael Charles (TD) |
| Trésorier Général                       | Ateby Yannick (TD), Koné Adams (TD) |
| Resp. Production Digitale & Communication | Dagbo Christ-Phanuel (TC2) |
| Resp. Contrôle Fiscal & Administratif   | Koffi Mohaye Lyvan Ange (TC2) |
| Resp. Commission Mentorat & Carrière    | Ama Erica (TD), Koné Isaac Hérèdé (TD), Adja Pierre Samuel (TD), Tanoh Aimé Sylvestre (TD) |
| Resp. Commission Événements & Vie associative | Douati Dylane (TD) |

> **À noter :**
> - Les présentations d'**Ouattara Ibrahim Nassir** (Président) et de **Dagbo
>   Christ-Phanuel** (Communication) ont été **rédigées à leur demande** ; toutes les
>   autres lettres sont reproduites telles que leurs auteurs les ont écrites.
> - **Tanoh Aimé Sylvestre** figure sur le bulletin parmi les candidats au poste de
>   Trésorier, mais sa lettre postule pour Mentorat & Carrière ; il est donc présenté
>   sous **Mentorat & Carrière** (choix validé).

## Ajouter ou modifier une présentation

Tout se passe dans le tableau `CANDIDATS`, dans le `<script>` en bas de `index.html`.
Chaque entrée suit ce modèle :

```js
{
  poste: 'president',            // id du poste : president | secretaire | tresorier |
                                 //   communication | gouvernance | mentorat | evenements
  name: 'Prénom Nom',            // nom affiché
  role: 'Président',             // libellé du rôle (badge)
  formation: 'Diplôme — École',  // ligne « formation » (optionnelle)
  letter: [                      // la lettre, paragraphe par paragraphe
    `Premier paragraphe…`,
    `Deuxième paragraphe…`,
    // liste à puces (facultatif) :
    { priorities: 'Mes priorités :', list: [ `Point 1`, `Point 2` ] },
  ],
  sign: 'PRÉNOM NOM',            // signature en bas de la lettre
  // note: 'Texte optionnel en italique sous la signature.'
}
```

Conseils :

- Écrivez chaque paragraphe entre **accents graves** ( `` ` `` ) : inutile d'échapper les apostrophes.
- Pour **ne rien couper**, collez le texte tel quel, en séparant simplement les paragraphes.
- Les statistiques du haut de page (nombre de présentations, de postes concernés)
  se **recalculent automatiquement**.

### Ajouter un nouveau poste

Ajoutez une entrée dans le tableau `POSTES` (id, `group`, `kind`, `icon`, `title`,
`mission`, `roles`). Les icônes disponibles sont listées dans l'objet `ICONS`
(`crown`, `doc`, `coins`, `mega`, `shield`, `grad`, `cal`).

## Personnalisation rapide

- **Couleurs / police** : variables CSS `:root` en haut de `index.html`
  (`--navy`, `--gold`, `--cream`, `--font`).
- **Textes d'introduction** : sections `.hero`, `#bureau`, `#commissions` et le
  bloc de clôture.

Le style suit un parti pris **éditorial** (filets fins plutôt que pilules colorées,
encadrés « dossier », barre de statistiques, badges plats) pour un rendu soigné et
« sur-mesure ». Ce système est documenté dans le skill Claude **`alex-brand`**
(`~/.claude/skills/alex-brand/`), réutilisable pour tout futur support A-LEX.

---

*Association des Anciens Élèves du LEAO — Rigueur · Discipline · Excellence · Fraternité · Solidarité.*
