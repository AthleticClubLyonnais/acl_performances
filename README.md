# ACL – Performances & records

Tableau de bord de l'Athletic Club du Lyonnais : performances de la semaine, distribution historique épreuve par épreuve, fiche athlète, comparaison de trajectoires par année de catégorie et records du club.

**Page en ligne : https://athleticclublyonnais.github.io/acl_performances/**

**Usage interne au club.** Le tableau de bord contient des noms d'athlètes, dont des mineurs. Voir la section Confidentialité avant toute publication.

## Contenu du dépôt

```
site/
  index.html     page unique : HTML, CSS, JavaScript, logo et données intégrés (aucune dépendance externe)
  robots.txt     demande aux moteurs de recherche de ne pas indexer
  .nojekyll      désactive Jekyll sur GitHub Pages
.github/workflows/pages.yml   déploiement automatique sur GitHub Pages
```

## Utilisation locale

Ouvrir `site/index.html` dans un navigateur (double-clic). Aucun serveur ni connexion n'est nécessaire.

## Publication sur GitHub Pages

1. Pousser le dépôt sur GitHub (branche `main`).
2. Dans **Settings → Pages**, choisir **Source : GitHub Actions**.
3. Chaque *push* qui modifie `site/` déclenche le workflow `Déploiement GitHub Pages` ; la page est disponible à l'adresse **https://athleticclublyonnais.github.io/acl_performances/** (rappelée aussi à la fin de l'exécution, onglet **Actions**).

Si le déploiement échoue avec « No artifacts named github-pages were found », vérifier que le workflow utilise `actions/upload-pages-artifact@v4`, puis relancer avec **Re-run all jobs**.

## Mise à jour des données

Les données (performances SI-FFA, records) sont intégrées dans `site/index.html`. Pour les mettre à jour :

1. Extraire la saison depuis SI-FFA (export « Ecran »), corriger l'extract, comparer aux records.
2. Régénérer le fichier `ACL_performances_records.html`.
3. Le copier dans `site/index.html` (en conservant la balise `<meta name="robots" ...>`), puis `git commit` et `git push`.

## Règles de calcul

- Quantile : part des performances de la même épreuve, du même sexe et de la même catégorie que la performance dépasse (égalités pour moitié).
- Vent supérieur à +2,0 m/s (50 m à 200 m, haies, longueur, triple saut) : performance conservée, exclue des records, classements et records personnels.
- Chronos manuels convertis en équivalent électronique ; salle et plein air séparés.
- Année de catégorie = saison (année de fin) moins année de naissance (BE1, BE2, MI1…).
- Historique : AC Tassin de 2003 à 2019, puis ACL et ses sections (ACT, ACD, ACM) depuis 2020 ; ACD présent depuis 2020, ACM depuis 2025 ; aucune donnée avant 2003.

## Confidentialité (RGPD)

- **GitHub Pages est public par défaut**, même pour un dépôt privé, sauf offre GitHub Enterprise Cloud (Pages à accès restreint). Ne pas publier cette page telle quelle sur Internet.
- Le fichier contient les noms de 1 894 athlètes, dont des mineurs, avec leurs performances, lieux et dates. Les années de naissance sont utilisées par le calcul des catégories.
- Options : héberger derrière un accès protégé (Cloudflare Access, Netlify avec mot de passe, serveur du club), ne diffuser le fichier qu'aux coachs et au bureau, ou publier une version allégée (records et faits marquants, athlètes mineurs anonymisés).
- `robots.txt` et `noindex` limitent l'indexation par les moteurs de recherche mais ne protègent pas l'accès.

## Licence

Usage interne ACL. Données issues de SI-FFA (FFA).
