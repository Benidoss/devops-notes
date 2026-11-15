# Bash : variables, conditions, boucles, fonctions, codes de retour et tâches planifiées avec cron

Un script Bash, c'est simplement un fichier qui contient les commandes que vous auriez tapées à la main.
Elles sont exécutées les unes après les autres, avec en plus des variables, des conditions et des boucles.

## 1. Les bases d'un script
```bash
"#!/bin/bash"          # le « shebang » : indique quel programme doit lire le script (toujours sur la 1re ligne, sans guillemets)
set -euo pipefail    # arrête le script dès qu'une commande échoue (-e), qu'une variable n'existe pas (-u) ou qu'une commande d'un pipeline échoue (-o pipefail)
```

> [!WARNING]
> `set -u` ne protège que d'une variable **qui n'existe pas**. Une variable qui existe mais qui est **vide** passe sans erreur : `rm -rf "$DOSSIER"/*` deviendrait alors `rm -rf /*`.\
> Il faut donc aussi tester la variable avec `[ -z "$DOSSIER" ]` avant toute suppression.

## 2. Variables
```bash
SEUIL=80                    # déclarer une variable et lui affecter une valeur : pas d'espace autour du =
DATE=$(date "+%Y-%m-%d")    # $( ... ) récupère le résultat d'une commande
echo "Seuil : $SEUIL"       # utiliser la variable avec $
```

Autres exemples de `$( ... )` :
```bash
DISK=$(df / --output=pcent | tail -1 | tr -d ' %')            # % d'occupation du disque /
MEMORY=$(free | awk '/Mem:/ {printf "%d", $3/$2*100}')        # % de mémoire utilisée
CPU=$(cut -d' ' -f1 /proc/loadavg)                            # charge CPU moyenne sur 1 minute
```

## 3. Les structures de contrôle

Elles contrôlent l'ordre d'exécution du script. Sans elles, les commandes s'exécutent simplement les unes après les autres, de haut en bas.

- Structure conditionnelle : `if`
```bash
if [ "$A" -gt "$B" ]; then ...; fi    # si A est plus grand que B, alors ...
```

- Structure itérative : `for`
```bash
for i in {1..10}; do ...; done        # répète ... pour i allant de 1 à 10
```

- Les opérateurs de comparaison de nombres :
```bash
-eq : égal
-ne : différent
-gt : plus grand que
-ge : plus grand ou égal
-lt : plus petit que
-le : plus petit ou égal
```

## 4. Fonctions

- Déclarer et appeler une fonction
- Le principe « décider, stocker, afficher » avec `ETAT` (DRY)


## 5. Organiser un projet

Plutôt que d'écrire les réglages en dur dans chaque script, on peut les regrouper dans un seul fichier, utilisé par tous les scripts. Pour changer la valeur d'une variable ou un dossier, on ne modifie que ce fichier.

- `source` : cette commande charge le fichier de configuration dans le script.

Quand cron lance le script, il ne se trouve pas « dans » le dossier du projet. Les chemins relatifs comme `config/...` ne fonctionnent donc plus. La solution : `SCRIPT_DIR`, qui contient le dossier où se trouve le script.
```bash
SCRIPT_DIR="$(cd "$(dirname "$0")" && pwd)"
source "$SCRIPT_DIR/config/maintenance.conf"
```

## 6. Sauvegarde et rotation
```bash
tar -czf archive.tar.gz dossier/    # créer une archive compressée (c = créer, z = compresser, f = fichier)
tar -tzf archive.tar.gz             # lister le contenu d'une archive, pour vérifier
[ -d "$DOSSIER" ]                   # vrai si le dossier existe (d = directory, dossier)
[ -z "$VARIABLE" ]                  # vrai si la variable est VIDE (z = zéro caractère)
ls -1t                              # lister un fichier par ligne, du plus récent au plus ancien
tail -n +8                          # afficher à partir de la 8e ligne
xargs -r rm --                      # supprimer chaque fichier reçu (-r : ne rien faire si la liste est vide)
$(( NB + 1 ))                       # faire un calcul
```

## 7. Redirections et journaux
- `>` / `>>` / `2>&1` / `| tee -a`

## 9. Vérifier la qualité avec shellcheck

`shellcheck` est un outil qui relit les scripts Bash et signale les erreurs et les mauvaises pratiques.
