# Cheat Sheet : `git reset` vs `git revert`

| Caractéristique            | `git reset`                                | `git revert`                                          |
| -------------------------- | ------------------------------------------ | ----------------------------------------------------- |
| **Fonction**               | Déplace le pointeur de la branche          | Crée un nouveau commit qui annule un commit           |
| **Historique des commits** | Modifie l'historique                       | Conserve l'historique                                 |
| **Types d'annulations**    | Annulation locale (non publiée)            | Annulation publique                                   |
| **Options principales**    | `--soft`, `--mixed`, `--hard`              | `-m <parent>` pour merge commits                      |
| **Effet sur les fichiers** | Peut garder ou supprimer les modifications | Garde les modifications, les annule seulement         |
| **Usage typique**          | Réinitialiser l'état d'une branche         | Annuler un commit spécifique sans perdre l'historique |
| **Sécurité en équipe**     | Peut causer des problèmes si déjà partagé  | Sûr pour une utilisation en collaboration             |

## Commandes Courantes

- **`git reset`** :
  - `git reset --soft HEAD~1` : Annule le dernier commit, garde les changements dans l'index.
  - `git reset --mixed HEAD~1` : Annule le dernier commit, garde les changements dans le répertoire de travail.
  - `git reset --hard HEAD~1` : Annule le dernier commit et supprime les changements.

- **`git revert`** :
  - `git revert <commit_hash>` : Crée un commit pour annuler le commit spécifié.
  - `git revert -m 1 <merge_commit_hash>` : Annule un merge commit en choisissant le premier parent.

## Quand utiliser quoi ?

- **Utilisez `git reset`** lorsque vous voulez annuler des commits récents sur une branche locale.
- **Utilisez `git revert`** pour annuler des commits dans un projet partagé sans modifier l'historique.
