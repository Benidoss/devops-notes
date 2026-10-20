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
  `ia.txt` in science_of_ia.txt                                                           # mv file.txt new_file.txt
  Still using `mv` I moved the file `devops.txt` in folder `rh`                           # mv devops.txt ../rh/
```

### Others small advanced tips with ``mv``
```bash
  `mv` rapport.txt ../rh/rapport_2026.txt                                                 # move et modify
  `mv` fichier1.txt fichier2.txt ../rh/                                                   # plusieurs fichiers vers un dossier
  `mv` *.txt ../rh/                                                                       # tous les .txt du dossier actuel
```


  > [!WARNING]
  > `mv` écrase sans prévenir un fichier qui porte déjà le même nom dans la destination.
  > Ajoutez `-i` (*interactive*) pour que `mv` demande confirmation avant d'écraser :
  >
  > ```bash
  >       mv -i rapport.txt ../rh/
  > ```



## Other useful commands and advanced tips

```bash
    
  `pwd`                                                                                   # où suis-je ?
  `ls -la`                                                                                # lister, y compris les fichiers cachés, avec les détails
  `cd / cd .. / cd ~`                                                                     # se déplacer
  `mkdir -p a/b/c`                                                                        # créer des dossiers (-p : crée aussi les parents)
  `touch fichier.txt`                                                                     # créer un fichier vide
  `cp / mv / rm`                                                                          # copier / déplacer ou renommer / supprimer
  `cat / less / head / tail`                                                              # lire un fichier (less : q pour quitter)
  `nano fichier.txt`                                                                      # éditer un fichier dans le terminal (Ctrl+O sauver, Ctrl+X quitter)
  `find ~ -name "*.txt"                                                                   # chercher des fichiers
  `grep "mot" fichier.txt`                                                                # chercher du texte dans un fichier

```