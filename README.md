# GUIDE CHEZ MOI

## CHANGEMENTS DANS LES FICHIERS

### Update des fichiers chezmoi

Pour mettre à jour les dotfiles : 

`~/.local/share/chezmoi/dot_XXX`

OU

`chezmoi edit ~/.XXX` (pas de dot ici, fichier d'origine local)



### Voir les diffs et changements local

`chezmoi diff` -> voir les diffs entre fichiers local et version chezmoi

`chezmoi -v apply` -> appliquer les changements au fichier original local



### Push les changements au repo

`git add .`

`git commit -m "commit message"`

`git push -u origin main`



## AJOUT DE NOUVEAUX FICHIERS

```
chezmoi add ~/.newdotfile
chezmoi cd
git add .
git commit -m "<New dotfile commit message>"
git push -u origin main
```

## UTILISATION SUR UNE AUTRE MACHINE

`sh -c "$(curl -fsLS chezmoi.io/get)" -- init --apply DrPulse` -> initialisation du repo


`chezmoi diff` -> vérification des diffs entre le repo et local

`chezmoi apply` -> si la config est bonne



## PULL ET APPLY LES DERNIERS CHANGEMENTS

Si besoin utiliser `chezmoi update -v` pour pull et apply les dernières config du repo


## DOC
https://jerrynsh.com/how-to-manage-dotfiles-with-chezmoi/
