# Les commandes de gestion de fichier dans Linux

With the command **mkdir** :                # mkdir new_folder
   -I created the folders : 
    "**exercises**" then, "**entreprise**" 
    "**accounting,rh,computerScience**"     # mkdir -p entreprises/{accounting,rh,computerScience}.txt

With the command **touch**, I created in folder "**computerScience**" the files **.txt** such as :
    **development.txt, devops.txt, ia.txt** # touch file.txt

  Using commamd **mv**, I modified the file **ia.txt** in **science_of_ia.txt**     # mv file.txt new_file.txt
  Still using **mv** I moved the file **devops.txt** in folder **rh**            # mv devops.txt ../rh/


**Other useful commands and advanced tips**

touch rapport_{lundi,mardi,mercredi}.txt   # crée 3 fichiers 
mkdir semaine{1..8}                        # crée semaine1 à semaine8 ({1..8} = suite de nombres)

mv rapport.txt ../rh/rapport_2026.txt      # déplacer et renommer

mv fichier1.txt fichier2.txt ../rh/   # plusieurs fichiers vers un dossier
mv *.txt ../rh/                       # tous les .txt du dossier actuel

> [!WARNING]
> **`mv` écrase sans prévenir** un fichier qui porte déjà le même nom dans la destination.
> Ajoutez `-i` (*interactive*) pour que `mv` demande confirmation avant d'écraser :
>
> ```bash
> mv -i rapport.txt ../rh/
> ```
# mv -i rapport.txt ../rh/
