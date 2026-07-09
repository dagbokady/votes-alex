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
│   └── logo.png        # Écusson A-LEX (fond détouré, transparent)
└── README.md           # Ce fichier
```

## Postes présentés

Les postes et leurs missions/rôles proviennent du document officiel
« Rôles & missions ». Les présentations reçues sont réparties ainsi :

| Poste                                   | Groupe        | Présentations |
|-----------------------------------------|---------------|---------------|
| Président & Vice-Président              | Bureau        | Ouattara Nassir (Président), Tapé Jo (Vice-Président) |
| Secrétaire Général                      | Bureau        | Droh Michael |
| Trésorier Général                       | Bureau        | Ateby Yannick, Koné Adams |
| Resp. Production Digitale & Communication | Bureau      | Dagbo Kady |
| Responsable de la Bonne Gouvernance     | Bureau        | Koffi Mohaye Lyvan Ange |
| Commission Mentorat & Carrière          | Commission    | Erica Ama, Koné Isaac, Adja Pierre Samuel, Tano Aimée Sylvestre |
| Commission Événements & Vie Associative | Commission    | Douati Dylane |

> **À noter :** les présentations d'**Ouattara Nassir** (Président) et de **Dagbo Kady**
> (Communication) ont été **rédigées à leur demande** ; toutes les autres lettres sont
> reproduites telles que leurs auteurs les ont écrites. Le poste **« Responsable de la
> Bonne Gouvernance »** ne figure pas dans l'organigramme initial : il a été ajouté car
> un membre s'est présenté pour ce rôle.

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

---

*Association des Anciens Élèves du LEAO — Rigueur · Discipline · Excellence · Fraternité · Solidarité.*
