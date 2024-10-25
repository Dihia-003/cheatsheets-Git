

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

#  Annuler des Commits et Merge Commits

## Annuler des Commits

### 1. Utiliser `git reset`

| Commande                   | Description                                                                    |
| -------------------------- | ------------------------------------------------------------------------------ |
| `git reset --soft HEAD~1`  | Annule le dernier commit, garde les changements dans l'index.                  |
| `git reset --mixed HEAD~1` | Annule le dernier commit, garde les changements dans le répertoire de travail. |
| `git reset --hard HEAD~1`  | Annule le dernier commit et supprime les changements (attention !).            |

### 2. Utiliser `git revert`

| Commande                   | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `git revert <commit_hash>` | Crée un nouveau commit qui annule le commit spécifié. |

## Annuler un Merge Commit

### 1. Utiliser `git revert`

| Commande                              | Description                                              |
| ------------------------------------- | -------------------------------------------------------- |
| `git revert -m 1 <merge_commit_hash>` | Annule un merge commit en choisissant le premier parent. |

### 2. Utiliser `git reset` (avec prudence)

| Commande                  | Description                                                        |
| ------------------------- | ------------------------------------------------------------------ |
| `git reset --hard HEAD~1` | Supprime le merge commit si c'est le dernier commit (attention !). |

## Notes Importantes

- **Contexte de travail partagé** : Préférez `git revert` pour éviter des problèmes avec l'historique partagé.
- **Sauvegardes** : Avant d'utiliser `git reset --hard`, assurez-vous d'avoir une sauvegarde de votre travail.

## Quand utiliser quoi ?

- **`git reset`** : Lorsque vous souhaitez annuler des commits récents sur une branche locale.
- **`git revert`** : Pour annuler des commits dans un projet partagé sans altérer l'historique.


Voici un cheatsheet en Markdown pour comprendre la différence entre `git log` et `git show` :



# Différence entre `git log` et `git show`

## `git log`
- **Description** : Affiche l'historique des commits.
- **Utilisation** :
  ```bash
  git log
  ```
- **Options courantes** :
  - `--oneline` : Affiche chaque commit sur une seule ligne.
    ```bash
    git log --oneline
    ```
  - `--graph` : Affiche un graphe ASCII de l'historique des branches.
    ```bash
    git log --graph --oneline
    ```
  - `-n <nombre>` : Limite le nombre de commits affichés.
    ```bash
    git log -n 5
    ```
  - `--author="<nom>"` : Filtre les commits par auteur.
    ```bash
    git log --author="Nom de l'Auteur"
    ```

## `git show`
- **Description** : Affiche les détails d'un commit spécifique.
- **Utilisation** :
  ```bash
  git show <commit_id>
  ```
- **Exemples** :
  - Afficher un commit spécifique :
    ```bash
    git show abc123
    ```
  - Afficher un commit et les changements en format diff :
    ```bash
    git show abc123 --stat
    ```

## Résumé
- **`git log`** : Pour explorer l'historique des commits.
- **`git show`** : Pour voir les détails et les changements d'un commit spécifique.

```


