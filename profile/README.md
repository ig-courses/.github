# Git IG

Orga contenant des repo **privés** permettant aux étudiants d'IG à Polytech d'avoir un espace de stockage pour les cours, TD, TP, annales & corrections, facile à transmettre et qui ne se perd pas comme un drive :slightly_smiling_face:

Ca permettra aussi de pouvoir travailler en offline au cas où pb de connexions

## Organisation

Pour éviter de mettre trop de charge sur 2 personnes et pour diversifier les sources, tout le monde aura les droits d'écriture sur les repos. Il faudra juste respecter l'organisation des fichiers.

Chaque année dispose d'un repo. Pour faciliter la recherche, adoptez cette arborescence (première idée pouvant être adaptée):

```txt
<yyyy>
 |- <S[5-9]> // S5, S6, S7, S8, S9
  |- <UE>
   |- <TD|TP|Cours|Annale> // un folder par catégorie
    |- <file_name>
    |- <file_name_corr> // pour le corrigé si besoin
```

### Corrections

Idéalement, avant d'upload les corrections, fusionnez les images en un seul pdf. A défaut, numérotez les dans l'ordre de lecture.

Enjoy ! 🧑‍💻

## Ajout automatisé d'étudiants (pour les admins)

Plutôt que d'entrer un par un les handles des étudiants, on peut utiliser la CLI de Github.

1. Installer la CLI de Github: [tuto d'install](https://github.com/cli/cli#installation)
2. S'authentifier: `gh auth login`
3. Récupérer les handles dans un fichier `handles` (un par ligne)
4. Ajouter les étudiants à l'orga:
   - Linux: utiliser `xargs` pour lire le fichier ligne par ligne et rajouter les étudiants à l'orga

        ```zsh
        xargs -a people -I {} zsh -c 'gh api -X PUT /orgs/ig-courses/memberships/{}' 
        ```

        Note: `-I {}` permet de dire que `{}` est le placeholder pour chaque ligne du fichier `people`. On aurait pu mettre autre chose que `{}` (comme `\m/` ou `V.v.V`)
   - Windows: 🤡
