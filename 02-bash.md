
# Bash : script bash, instruction, variable, commande, 

Un script Bash, c’est simplement un fichier qui contient des commandes que vous tapiez à la main. 
Elles sont exécutées les unes après les autres, avec en plus des variables, des conditions et des boucles.

## 1. Les bases d'un script
```bash
   "#!/bin/bash"                                  # Indique quel programme doit lire le script. 
   et -euo pipefail 
```

## 2. Variables
```bash
   SEUIL=80                                        # La déclaration d'une variable et l'affection d'une valeur à ce dernier se fait sans espaece autour.
   DATE=$(date "+%Y-%m-%d")                        # Pour récupérer le résultat d'une commande. Ex de commande : (date "+%Y-%m-%d"), (df / --output=pcent | tail -1 | tr -d ' %' ), (free | awk '/Mem:/ {printf "%d", $3/$2*100}'), (uptime | awk -F'load average: ' '{print $2}' | cut -d, -f1)
   echo "Seuil : $SEUIL"                           
```

## 3. Conditions
```bash
    if [ "$A" -gt "$B" ]; then ... fi                  # 
```
- Les opérateurs : 
```bash
    `-gt` : plus grand que, 
    `-lt` : plus petit,
    `-eg` : plus grand ou égal,
    `-eq` : égal.
```

## 4. Fonctions

- Déclarer et appeler une fonction
- Le principe « décider, stocker, afficher » avec `ETAT` (DRY)

## 5. Boucles

```bash
       for i in {1..10}; do ...; done
```

## 6. Organiser un projet

Plutôt que d’écrire les réglages en dur dans chaque script, on les regroupe dans un seul fichier. Pour changer un seuil ou un dossier, on ne touche qu’à cet endroit. 

- `source` : On utilise cette commande pour charger le fichier de config.

Quand cron lancera le script, il ne sera pas « dans » le dossier du projet. Les chemins relatifs comme config/... ne marcheront donc plus. La solution :  `SCRIPT_DIR` 

## 7. Sauvegarde et rotation
```bash
    tar -czf archive.tar.gz dossier/                # créer une archive compressée (c=créer, z=compresser, f=fichier)
    tar -tzf archive.tar.gz                         # lister le contenu d'une archive, pour vérifier
    [ -d "$DOSSIER" ]                               # vrai si le dossier existe (`d` = Dossier)
    [ -z "$VARIABLE" ]                              # vrai si la variable est VIDE (`z`= vide)
    ls -1t                                          # lister un fichier par ligne, du plus récent au plus ancien
    tail -n +8                                      # afficher à partir de la 8e ligne
    xargs -r rm --                                  # supprimer chaque fichier reçu (-r : ne rien faire si la liste est vide)
    $(( NB + 1 ))                                   # faire un calcul
```

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


## Vérifier la qualité avec shellcheck

`shellcheck` est un outil qui relit les scripts Bash et signale les erreurs et les mauvaises pratiques.

`-z` (vide), 
    `-d` (dossier existe), 
    `!` (inverse)