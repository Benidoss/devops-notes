# Les commandes de gestion de fichier dans Linux


## With the command ``mkdir`` :                
   I created the folders such as : 

  ```bash
    exercises then, entreprise 
    accounting,rh,computerScience    # mkdir -p entreprises/{accounting,rh,computerScience}.txt
  ```

### Others small advanced tips with ``mkdir``
mkdir week{1..8}                                                                       # creates week1 to week8 ({1..8} = nomber sequence)



## With the command ``touch``, 
I created in folder ``computerScience`` the files ``.txt`` such as :
  
  ``development.txt, devops.txt, ia.txt``                                               # touch file.txt

### Others small advanced tips with ``touch``
  touch rapport_{mondy,tuesday,wednesday}.txt                                           # one-click file creation
  


## With the command ``mv`` :
I modified the file ``ia.txt``**`` in ``**``science_of_ia.txt``                          # mv file.txt new_file.txt
Still using ``mv`` I moved the file ``devops.txt`` in folder ``rh``                      # mv devops.txt ../rh/

### Others small advanced tips with ``mv``
  mv rapport.txt ../rh/rapport_2026.txt                                                  # move et modify
  mv fichier1.txt fichier2.txt ../rh/                                                    # plusieurs fichiers vers un dossier
  mv *.txt ../rh/                                                                        # tous les .txt du dossier actuel

```bash
> [!WARNING]
> `mv` écrase sans prévenir un fichier qui porte déjà le même nom dans la destination.
> Ajoutez `-i` (*interactive*) pour que `mv` demande confirmation avant d'écraser :
>
> ```bash
>       mv -i rapport.txt ../rh/
> ```
```


## Other useful commands and advanced tips

