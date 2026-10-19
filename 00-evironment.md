# 00 – Mise en place de l'environnement

## Connexion SSH à la VM (VirtualBox)
La VM est en NAT : une redirection de port VirtualBox renvoie le port 2222 de Windows
vers le port 22 (SSH) de la VM.

```bash
ssh utilisateur@127.0.0.1 -p 2222   # Connexion à la VM depuis la machine hot
```

## Raccourci de connexion (~/.ssh/config sur Windows)
```
Host devops-lab
    HostName 127.0.0.1
    Port 2222
    User utilisateur
```
```bash
ssh devops-lab    # même connexion, grâce au raccourci
```

## Mettre à jour Ubuntu
```bash
sudo apt update            # met à jour la liste des paquets disponibles
sudo apt upgrade -y        # installe les mises à jour
ip a                       # affiche les adresses IP de la machine
```

## Configurer Git
```bash
git config --global user.name "Benoît Dosseh"   # nom affiché sur mes commits
git config --global user.email "mon_email"      # e-mail lié à mon compte GitHub
```

## Relier la VM à GitHub avec une clé SSH
```bash
ssh-keygen -t ed25519 -C "mon_email"   # crée une paire de clés (privée + publique)
cat ~/.ssh/id_ed25519.pub              # affiche la clé publique à coller dans GitHub
ssh -T git@github.com                  # teste la connexion à GitHub
```
La clé privée reste dans la VM ; seule la clé publique est donnée à GitHub
(Settings → SSH and GPG keys).

## Envoyer du code sur GitHub
```bash
git clone git@github.com:Benidoss/nom-du-depot.git   # récupère un dépôt
git add .                       # prépare les modifications
git commit -m "message"         # enregistre une version
git push                        # envoie sur GitHub
```