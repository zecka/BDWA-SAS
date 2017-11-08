# Pratique: Environnement de travail 2

Veuillez écrire un rapport de vos manipulations. Ce rapport a deux objectifs: il sert, dans un premier temps, à évaluer votre travail mais c'est également un support pour vous plus tard. Écrivez-le donc avec soin !

Le rapport doit être envoyé par le lien : https://www.dropbox.com/request/qxMqxOh2NJCGUs2U5tI2 avant le 7.10.17 à minuit.

Merci de nommer le fichier de cette manière : **Nom_Prénom_Rapport_2.pdf**.

## 1. Bash en ligne de commande

### 1.1 Se connecter en SSH sur un serveur distant

Connectez vous sur les serveurs que vous avez utilisé lors de la première semaine en SSH. Les identifiants sont les mêmes que pour le FTP qui vous ont été fournis. Attention, le port n'est pas le 22 (port par défaut de SSH) mais un numéro de port > 1000 qui vous a également été fourni. Si vous n'avez plus ces informations, il est possible de les redemander.

```
Voir dans les slides du cours
```



### 1.2 Commandes bash

Lister l'ensemble de commande qui permettent de faire les actions listées ci-dessous (il y a souvent plusieurs méthodes). Si le serveur distant est inaccessible, il est possible de réaliser ces commandes sur tout autre système Linux ou macOS et éventuellement Windows 10 (pas testé). Dans ce cas, merci de le préciser dans le rapport.

- Créer le dossier `/tmp/test` et placer dans ce dossier un fichier contenant le texte "Hello World", nommé *hello.txt* en utilisant la commande `echo`


```bash
cd /tmp
mkdir test
echo "Hello World" > hello.txt
```



- Copier le fichier dans un nouveau fichier *hello_cp.txt* en utilisant la commande `cp`

```bash
cp hello.txt hello_cp.txt
```



- Copier le fichier dans un nouveau fichier *hello_cat.txt* en utilisant la commande `cat`

```bash
cat hello.txt > hello_cat.txt
```



- Quelle est la commande permettant d'obtenir de l'aide sur n'importe quelle commande ? (elle n'est pas forcément disponible sur le serveur distant car il a une configuration minimale)

```bash
man <commande>
man ls
man echo
```



- Modifier le fichier *hello.txt* pour qu'il contienne *Hello <votre nom d'utilisateur>* en utilisant la commande `nano` ou `vi`.

```bash
nano hello.txt
# Modifier le fichier puis CTRL+O pour sauver, CTRL+X pour quitter
vi hello.txt
# "a" pour ajouter du contenu, modifier le fichier puis ESC + ":wq" pour écrire (w) et quitter (q)
```



- Visualiser l'adresse IP de votre système et l'écrire dans le rapport. Préciser s'il s'agit d'une adresse IPv4 ou IPv6 et si elle est publique ou privée.

```bash
ipconfig
# ou
ip addr
# ou
ip a
```



- Créer une archive de type *tarball* (.tar ou .tar.gz) avec le contenu du dossier `/tmp/test`. À quoi cela sert-il ?

```bash
tar cfz archive.tar.gz /tmp/test
# Créer une archive zippé facile contenant tous les fichiers, facile à déplacer
```



- Donner la version du noyau Linux de l'OS utilisé

```bash
uname -r # Donne uniquement la version du noyau Linux (r => release)
uname -a # Donne plein d'information sur le système
cat /proc/version # Similaire à uname -a
```



- Interdire la lecture, l'écriture et l'exécution du fichier *hello_cat.txt* à toute autre personne que vous en utilisant la commande `chmod` et la gestion des droits de manière binaire (un nombre en 0 et 7 pour chaque type d'utilisateur)

```bash
chmod 700 hello_cat.txt
```



- Autoriser l'exécution du fichier *hello_cp.txt* par tous les utilisateurs du système en utilisant `chmod` mais sans utiliser la gestion des droits de manière binaire.

```bash
chmod +x hello_cp.txt
# ou
chmod a+x hello_cp.txt
```



- Télécharger le fichier `https://raw.githubusercontent.com/Idnan/bash-guide/master/README.md` dans `/tmp/test`.

```bash
cd /tmp/test
wget https://raw.githubusercontent.com/Idnan/bash-guide/master/README.md
```



- Faire en sorte que quand on entre `l` dans le terminal, cela affiche la même chose que la commande `ls -laht`. Copier le résultat de cette commande dans le rapport pour le dossier `/tmp/test`.

```bash
alias l="ls -laht" # Uniquement pour le terminal courant
# Pour modifier dans tous les terminaux, il faut ajouter cela à /home/<user>/.bashrc
```



## 2. git & GitHub

1. Installer `git` sur votre ordinateur (https://git-scm.com/book/fr/v1/D%C3%A9marrage-rapide-Installation-de-Git)
2. Créer un compte sur GitHub si ce n'est pas déjà fait (https://github.com)
3. Forker le dépôt https://github.com/5ika/BDWA-SAS
4. Cloner votre fork sur votre ordinateur
5. Modifier le fichier README.md en rajoutant un lien vers votre compte GitHub tout en bas
6. Visualiser l'état de votre copie locale avec `git status`
7. Visualier les changements que vous avez effectué avec `git diff`
8. Ajouter le fichier README.md au *staging*
9. Visualiser l'état de votre copie locale avec `git status`
10. Créer un commit avec un message de commit clair et bref expliquant votre modification
11. Pousser votre modification sur GitHub
12. Proposer votre modification au dépôt principal en créant une nouvelle *Pull Request*.

En tant que propriétaire du dépôt principal, je vais ainsi pouvoir voir la modification que vous proposez. Si je suis d'accord avec cette modification, j'accepterais votre Pull Request et votre modification sera *mergée* dans le dépôt principal. Si non, je vous exliquerais ce qui ne joue pas dans la Pull Request pour que vous puissiez la corriger en vue d'être acceptée.