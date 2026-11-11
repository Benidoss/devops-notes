# 02 – Bash : écrire des scripts
Un script Bash, c’est simplement un fichier qui contient des commandes que vous tapiez à la main. 
Elles sont exécutées les unes après les autres, avec en plus des variables, des conditions et des boucles.

## 1. Les bases d'un script
```bash
   Le shebang `#!/bin/bash`                     # elle indique quel programme doit lire le script.
   chmod +x` / `./script.sh                     # Rendre exécutable et lancer un fichier par un ayant pas droit. 
   et -euo pipefail 
```

## 2. Variables
```bash
   SEUIL=80                                        # pas d'espace autour du 
   DATE=$(date "+%Y-%m-%d")                        # récupérer le résultat d'une commande (date "+%Y-%m-%d")
   echo "Seuil : $SEUIL"                           
```

## 3. Conditions
```bash
if [ "$A" -gt "$B" ]; then ... fi
```
- Les opérateurs : `-gt`, `-lt`, `-eq`, `-z` (vide), `-d` (dossier existe), `!` (inverse)

## 4. Fonctions
- Déclarer et appeler une fonction
- Le principe « décider, stocker, afficher » avec `ETAT` (DRY)

## 5. Boucles
```bash
for i in {1..10}; do ...; done
```

## 6. Organiser un projet
- `source` : charger un fichier de configuration
- `SCRIPT_DIR` : pourquoi un script doit trouver son propre dossier

## 7. Sauvegarde et rotation
- `tar -czf` / `tar -tzf`
- La chaîne `ls -1t | tail -n +8 | xargs -r rm --` expliquée étape par étape

## 8. Redirections et journaux
- `>` / `>>` / `2>&1` / `| tee -a`

## 9. Les 5 questions de compréhension
1. À quoi sert `set -euo pipefail` ?
2. Pourquoi chaque script charge-t-il lui-même la configuration ?
3. Pourquoi vérifier que `DOSSIER_SAUVEGARDES` n'est pas vide ?
4. Comment fonctionne la rotation ?
5. Que fait `2>&1 | tee -a` ?

## 10. Mes erreurs et ce que j'en retiens
- ...