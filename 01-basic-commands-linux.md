# Commandes de manipulation de fichiers


## Avec la commande `mkdir`
I created the folders such as :

```bash
exercises then, entreprises
accounting,rh,computerScience  # mkdir -p entreprises/{accounting,rh,computerScience}
```

### Autres astuces avancées avec `mkdir`
```bash
mkdir week{1..8}           # creates week1 to week8 ({1..8} = number sequence)
mkdir -p test/a/b/c        # dossiers imbriqués
mkdir -p test/{x,y,z}      # dossiers côte à côte
```


## Avec la commande `touch`
I created in folder `computerScience` the files `.txt` such as :
```bash
development.txt, devops.txt, ia.txt  # touch file.txt
```

### Autres astuces avancées avec `touch`
```bash
touch rapport_{monday,tuesday,wednesday}.txt  # one-click file creation
touch test/.secret                            # un fichier caché (le point au début)
```


## Avec la commande `mv`
I modified the file
```bash
ia.txt in science_of_ia.txt                              # mv file.txt new_file.txt
Still using mv I moved the file devops.txt in folder rh  # mv devops.txt ../rh/
```

### Autres astuces avancées avec `mv`
```bash
mv rapport.txt ../rh/rapport_2026.txt  # move and modify
mv fichier1.txt fichier2.txt ../rh/    # plusieurs fichiers vers un dossier
mv *.txt ../rh/                        # tous les .txt du dossier actuel
```

> [!WARNING]
> `mv` écrase sans prévenir un fichier qui porte déjà le même nom dans la destination.\
> Ajoutez `-i` (*interactive*) pour que `mv` demande confirmation avant d'écraser :

```bash
mv -i rapport.txt ../rh/
```


## Avec la commande `rm`
I removed the file
```bash
development.txt  # supprimer un fichier
```

### Autres astuces avancées avec `rm`
```bash
rm fichier1.txt fichier2.txt  # supprimer plusieurs fichiers
rm *.log                      # supprimer tous les fichiers .log du dossier
rmdir dossier                 # supprimer un dossier VIDE uniquement
rm -r dossier                 # supprimer un dossier ET tout son contenu (-r = récursif)
```

### Options utiles
> [!TIP]
> `i`	Demande confirmation pour chaque fichier. C’est la plus sûre.\
> `I`	Demande une seule confirmation si vous supprimez plus de 3 fichiers ou un dossier. C’est un bon compromis.\
> `v`	Affiche chaque fichier supprimé (verbose). On voit ce qui se passe.\
> `r`	Supprime les dossiers et leur contenu.\
> `f`	Force : aucune question, aucun message d’erreur.

### Les astuces de prudence

```bash
1 Vérifier avant de supprimer.
  ls *.log  # d'abord, voir ce qui correspond
  rm *.log  # ensuite, supprimer
2 Supprimer un fichier dont le nom commence par un tiret. Un fichier nommé -test.txt est pris pour une option. Ajoutez --, qui signifie « fin des options » :  # rm -- -test.txt

3 Supprimer un nom avec des espaces :  # rm "mon fichier.txt"
```

## Les dangers à connaître absolument
> [!CAUTION]
> `rm -rf` supprime tout, sans aucune question. Utilisez-le seulement quand vous êtes certain de la cible, et relisez la commande avant d’appuyer sur Entrée.

```bash
rm -rf ./dossier   # supprime "dossier" ✅
rm -rf . /dossier  # supprime TOUT le dossier actuel ❌ (un espace en trop !).
rm -rf "$DOSSIER"/*
```

# Commandes de création d'utilisateurs et de restriction des droits

Pour l'occasion, j'ai créé un dossier `partage` dans le répertoire `/srv` pour pouvoir faire intervenir les notions de propriétaires.
```bash
sudo mkdir /srv/partage
```

Puis, j'ai créé dans le dossier `partage` un fichier .txt : `consignes.txt` que j'ai pu éditer avec la commande :
```bash
sudo nano /srv/partage/consignes.txt
```

Afin de pouvoir mettre les droits sur le dossier ainsi que sur le fichier, j'ai créé un groupe d'utilisateurs :
```bash
sudo groupadd partage  # Commande pour créer un groupe (attention, ce n'est pas un dossier, plutôt un fichier sys qui se retrouve dans le répertoire /etc/).
```
Dans lequel j'ai mis mon utilisateur `trainee` via la commande :
```bash
sudo usermod -aG partage trainee
```
Que j'ai créé avec la commande :
```bash
sudo adduser trainee  # Commande pour ajouter un utilisateur.
```

Et j'y ai mis des droits de `lecture` et d'`exécution` en donnant au groupe `partage` le dossier `partage` qui se trouve dans `/srv`, ainsi que le fichier qui s'y trouve :
```bash
sudo chown root:partage /srv/partage
sudo chown root:partage /srv/partage/consignes.txt
```
Voici les droits en question :
```bash
sudo chmod 750 /srv/partage                # pour le groupe partage, j'ai mis sur le dossier des droits de lecture et d'exécution.
sudo chmod 640 /srv/partage/consignes.txt  # pour le groupe partage, j'ai mis sur le fichier des droits de lecture uniquement.
```

### Bon à savoir
Il faut toujours se poser les questions suivantes avant d'agir :

> [!TIP]
> Dans quelle catégorie tombe votre nouvel utilisateur (propriétaire, groupe ou autres) ?\
> Quels droits cette catégorie doit-elle avoir sur le dossier (pour entrer) ?\
> Et sur le fichier (pour lire sans modifier) ?

Pour tester la restriction, on passe en mode `trainee`, un des utilisateurs s'il y en a d'autres dans le groupe `partage` :
```bash
su - trainee  # commande pour switch à un autre utilisateur (exit pour revenir).
```

![Test : sur l'image on voit la prise de main du trainee et son accès au dossier partage qui est la propriété du root](images/connexion_acces.png)


![Test : trainee ne peut pas modifier le fichier](images/modification_impossible.png)


## Commandes de gestion des utilisateurs
```bash
w                           # Shows which users are logged in.
sudo deluser <username>     # Deletes a user.
sudo passwd <username>      # Sets or changes the password for a user.
sudo passwd -l <username>   # Locks a user account.
sudo passwd -u <username>   # Unlocks a user password.
sudo chage <username>       # Sets user password expiration date.
```

## Commandes de gestion des groupes
```bash
id [username]               # Displays user and group IDs.
groups [username]           # Shows the groups a user belongs to.
sudo addgroup <groupname>   # Creates a new group.
sudo delgroup <groupname>   # Deletes a group.
```


## Autres commandes utiles et astuces avancées

```bash
pwd                                                     # où suis-je ?
ls -la                                                  # lister, y compris les fichiers cachés, avec les détails
ls -l                                                   # lister avec les détails (sans les fichiers cachés)
ls -a test                                              # .secret apparaît
cd / cd .. / cd ~                                       # se déplacer
touch fichier.txt                                       # créer un fichier vide
cp / mv / rm                                            # copier / déplacer ou renommer / supprimer
cat / less / head / tail                                # lire un fichier (less : q pour quitter)
find ~ -name "*.txt"                                    # chercher des fichiers
grep "mot" fichier.txt                                  # chercher du texte dans un fichier
sudo setfacl -m u:trainee:r /srv/partage/consignes.txt  # pour donner des droits à un seul utilisateur.
```


# Paquets, processus, services et surveillance

## Les paquets
`apt` est le gestionnaire de paquets d’Ubuntu permettant de télécharger et d'installer les logiciels depuis leurs dépôts officiels.

```bash
sudo apt update                   # pour mettre à jour la liste des logiciels disponibles
apt search nom_logiciel           # pour chercher un logiciel
sudo apt install nom_logiciel -y  # pour installer (-y : répond oui automatiquement)
sudo apt remove nom_logiciel      # pour désinstaller un logiciel
```

### Autres commandes avec `apt`
```bash
sudo apt install -f --reinstall <package>  # Reinstalls a broken package.
apt-cache policy <package>                 # Lists available package versions.
sudo apt upgrade                           # Upgrades all upgradable packages.
sudo apt purge <package>                   # Removes a package and all its configuration files.
```


## Les services
Pour gérer les services, qui sont des programmes qui tournent en permanence en arrière-plan, on utilise `systemctl` :

```bash
sudo systemctl status nom_logiciel   # est-il actif ? (q pour quitter)
sudo systemctl stop nom_logiciel     # l'arrêter
sudo systemctl start nom_logiciel    # le démarrer
sudo systemctl restart nom_logiciel  # le redémarrer (après un changement de configuration)
sudo systemctl enable nom_logiciel   # le lancer automatiquement au démarrage du serveur
```

### Commandes de gestion des services
```bash
sudo systemctl reload <service>  # Reloads a service’s configuration without interrupting its operation.
journalctl -f                    # Follows the journal, showing new log messages in real time.
journalctl -u <unit_name>        # Displays logs for a specific systemd unit.
```


## Les processus
Un processus est un programme en cours d’exécution. Chacun a un numéro unique, le PID.

```bash
ps aux               # Commande pour voir tous les processus en cours
ps aux | grep nginx  # seulement ceux de nginx
top                  # vue en direct, triée par consommation (q pour quitter)
kill PID             # demander à un processus de s'arrêter
```

## Les logs
Quand un service plante, la réponse est presque toujours dans les journaux. Les lire, c’est le premier réflexe d’un DevOps.

```bash
journalctl -u nginx                       # journaux du service nginx
journalctl -u nginx --since today         # seulement aujourd'hui
sudo tail -f /var/log/nginx/access.log    # suivre les visites en direct (Ctrl+C pour sortir)
```

## Surveillance de la machine

```bash
df -h        # espace disque (-h : en Go/Mo, lisible par un humain)
du -sh ~/*   # taille de chaque dossier dans ~
free -h      # mémoire vive utilisée et libre
uptime       # depuis quand le serveur tourne + charge
```
