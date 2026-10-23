# File manipulation commands


## With the command ``mkdir`` :                
   I created the folders such as : 

  ```bash
    exercises then, entreprise 
    accounting,rh,computerScience                                                      # mkdir -p entreprises/{accounting,rh,computerScience}.txt
  ```

### Others small advanced tips with ``mkdir``
```bash
  mkdir week{1..8}                                                                        # creates week1 to week8 ({1..8} = nomber sequence)
```


## With the command ``touch``, 
I created in folder ``computerScience`` the files ``.txt`` such as :
  ```bash
  development.txt, devops.txt, ia.txt                                                     # touch file.txt
  ```

### Others small advanced tips with ``touch``
```bash
  touch rapport_{mondy,tuesday,wednesday}.txt                                             # one-click file creation
```
  


## With the command `mv` :
I modified the file 
```bash
  ia.txt in science_of_ia.txt                                                             # mv file.txt new_file.txt
  Still using mv I moved the file devops.txt in folder rh                                 # mv devops.txt ../rh/
```

### Others small advanced tips with ``mv``
```bash
  mv rapport.txt ../rh/rapport_2026.txt                                                 # move et modify
  mv fichier1.txt fichier2.txt ../rh/                                                   # plusieurs fichiers vers un dossier
  mv *.txt ../rh/                                                                       # tous les .txt du dossier actuel
```


  > [!WARNING]
  > `mv` écrase sans prévenir un fichier qui porte déjà le même nom dans la destination.\
  > Ajoutez `-i` (*interactive*) pour que `mv` demande confirmation avant d'écraser :
  
  ```bash
         mv -i rapport.txt ../rh/
  ```


## With the command ``rm``
I removed the file 
``` bash
    development.txt                                                                        # supprimer un fichier 
```

### Others small advanced tips with ``rm`` 
```bash
  rm fichier1.txt fichier2.txt                                                             # supprimer plusieurs fichiers
  rm *.log                                                                                 # supprimer tous les fichiers .log du dossier
  rmdir dossier                                                                            # supprimer un dossier VIDE uniquement
  rm -r dossier                                                                            # supprimer un dossier ET tout son contenu (-r = récursif)

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
    ls *.log                                                                               # d'abord, voir ce qui correspond
    rm *.log                                                                               # ensuite, supprimer 
  2 Supprimer un fichier dont le nom commence par un tiret. Un fichier nommé -test.txt est pris pour une option. Ajoutez --, qui signifie « fin des options » :                                                           # rm -- -test.txt

  3 Supprimer un nom avec des espaces :                                                    # rm "mon fichier.txt"  
```

## Les dangers à connaître absolument
> [!CAUTION]

`rm -rf`  supprime tout, sans aucune question. Utilisez-le seulement quand vous êtes certain de la cible, et relisez la commande avant d’appuyer sur Entrée.\

      ```bash
        rm -rf ./dossier     # supprime "dossier" ✅
        rm -rf . /dossier    # supprime TOUT le dossier actuel ❌ (un espace en trop !)
        rm -rf "$DOSSIER"/*
        
      ```


## Other useful commands and advanced tips

```bash   
  pwd                                                                                    # où suis-je ?
  ls -la                                                                                 # lister, y compris les fichiers cachés, avec les détails
  ls -l                                                                                  # lister les fichier cahi
  cd / cd .. / cd ~                                                                      # se déplacer
  mkdir -p a/b/c                                                                         # créer des dossiers (-p : crée aussi les parents)
  touch fichier.txt                                                                      # créer un fichier vide
  cp / mv / rm                                                                           # copier / déplacer ou renommer / supprimer
  cat / less / head / tail                                                               # lire un fichier (less : q pour quitter)
  nano fichier.txt                                                                       # éditer un fichier dans le terminal (Ctrl+O sauver, Ctrl+X quitter)
  find ~ -name "*.txt"                                                                   # chercher des fichiers
  grep "mot" fichier.txt                                                                 # chercher du texte dans un fichier
```

```bash
  cd ~
  mkdir -p test/a/b/c        # dossiers imbriqués
  mkdir -p test/{x,y,z}      # dossiers côte à côte
  touch test/.secret         # un fichier caché (le point au début)
  ls test                    # .secret n'apparaît pas
  ls -a test                 # .secret apparaît∟
  sudo adduser stagiaire     # créer un utilisateur (interactif, crée son dossier /home)
  sudo groupadd equipe       # créer un groupe
  sudo usermod -aG equipe stagiaire    # ajouter stagiaire au groupe equipe
  su - stagiaire             # devenir stagiaire (exit pour revenir)
```
