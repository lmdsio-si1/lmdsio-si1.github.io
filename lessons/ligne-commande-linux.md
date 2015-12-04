---
layout: post
title: La ligne de commande sous Linux
---

## Généralités

La **ligne de commande** est une interface textuelle pour piloter le système d'exploitation d'un ordinateur. Pour accéder à la ligne de commande, on utilise un **terminal**, appelé également **console**.

Les fichiers et répertoires d'un ordinateur forment une arborescence appelée **système de fichiers** (*filesystem*). Le point de départ du système de fichiers est un répertoire appelé **racine**, notée `/` (*slash*) sous Linux. Chaque répertoire peut contenir des fichiers ainsi que des sous-répertoires.

![](../assets/ligne-commande-linux/codecademy-cmdline-filesystem-small.png)
{:.centered}

## Naviguer dans le système de fichiers

### Chemin absolu, chemin relatif

L'emplacement de chaque ressource (fichier ou répertoire) dans le système de fichiers est appelé son **chemin**. Dans un chemin Linux, le séparateur dans entre deux répertoires est le caractère `/`.

On distingue deux types de chemins :

* Un chemin **absolu** identifie une ressource en commençant à la racine de l'arborescence, avec le caractère `/`. Un chemin absolu ne dépend pas du répertoire courant et est donc valide partout.

    * `/home/baptiste/hello.txt` et `/etc/apache/httpd.conf` sont des exemples de chemins absolus.

* Un chemin **relatif** identifie une ressource à partir du répertoire courant. Il dépend donc du répertoire courant et n'est pas valide partout.

    * `../marc/adresses.txt` et `documents/cours/si1.pdf` (sans `/` au début !) sont des exemples de chemins relatifs.

### Répertoire personnel

Sous Linux, chaque utilisateur (sauf `root`) dispose d'un répertoire personnel à son nom situé dans `/home`. Par exemple, le répertoire personnel de l'utilisateur `nicolas` est `/home/nicolas`.

Le chemin absolu du répertoire personnel peut s'écrire de manière abrégée avec le caractère `~` (*tilde*). Par exemple, le chemin `~/music/` pour l'utilisateur `nicolas` correspond au chemin absolu `/home/nicolas/music/`.

### Commandes à connaître

* `pwd` (*print working directory*) affiche le chemin du répertoire courant.

* `ls` (*list*) affiche le contenu du répertoire courant.

* `cd` (*change directory*) permet de se déplacer dans le système de fichiers en changeant de répertoire courant. 

    * `cd monrep` fait du répertoire `monrep` le répertoire courant.
    * `cd ..` permet de remonter d'un niveau dans l'arborescence.
    * `cd /` permet de revenir à la racine de l'arborescence.
    * `cd` permet de revenir à la racine du répertoire personnel.

### Options des commandes

Presque toutes les commandes Linux acceptent des **options** qui modifient leur comportement. Voici par exemple les options de la commande `ls` :

* `ls -a` affiche également les fichiers cachés, qui commencent par un `.` sous Linux.
* `ls -l` affiche des informations supplémentaires, comme la date et la taille des fichiers.
* `ls -t` trie les fichiers par ordre de dernière modification.

Les options d'une commande peuvent être combinés. Exemple : `ls -alt`.

## Modifier le système de fichiers

### Commandes à connaître

* `mkdir` (*make directory*) crée un nouveau répertoire.

    * `mkdir monrep` crée le répertoire `monrep` dans le répertoire courant.

* `touch` crée un nouveau fichier (vide) ou met à jour la date de modification d'un fichier existant. 

    * `touch fic1.txt` crée un fichier vide `fic1.txt` dans le répertoire courant.

* `cp` (*copy*) copie des fichiers ou des répertoires. 

    * `cp fic1.txt monrep/` copie le fichier `fic1.txt` dans le répertoire `monrep`. 
    * `cp fic1.txt fic2.txt` duplique le fichier `fic1.txt` sous le nom `fic2.txt`.

* `mv` (*move*) déplace ou renomme des fichiers ou des répertoires. 

    * `mv fic1.txt monrep/` déplace le fichier `fic1.txt` dans le répertoire `monrep`.
    * `mv fic1.txt fic2.txt` renomme le fichier `fic1.txt` en `fic2.txt`.

* `rm` (*remove*) supprime des fichiers. `rm -r` supprime des répertoires.

    * `rm fic1.txt` supprime le fichier `fic1.txt`.
    * `rm -r monrep` supprime le répertoire `monrep` ainsi que tout son contenu.

### Caractère générique

Le caractère générique `*` (*wildcard*) permet de remplacer une partie d'un nom de fichier ou de répertoire. On l'utilise pour appliquer une commande à plusieurs éléments.

* `cp f*.txt monrep/` copie dans le répertoire `monrep` tous les répertoires dont le nom commence par un `f` et finit par `.txt`.
* `rm *` supprime tous les fichiers du répertoire courant.

## Affichage et édition de fichiers

### Commandes à connaître

* `echo` affiche un texte.

    * `echo "Bonjour Monde"` affiche le texte "Bonjour Monde".

* `cat` affiche le contenu d'un fichier.

    * `cat monfic` affiche le contenu du fichier `monfic`.

* `nano` lance un éditeur de texte nommé **Nano**. Il dispose de plusieurs raccourcis clavier, dont :

    * `Ctrl+O` pour sauvegarder un fichier.
    * `Ctrl+X` pour quitter l'éditeur.

* `clear` réinitialise le contenu de la console.

### Redirections

Le caractère `>` permet de rediriger la sortie d'une commande vers un fichier **en écrasant son contenu actuel**. 

Le caractère `>>` redirige la sortie d'une commande vers un fichier **en l'ajoutant à la fin de son contenu actuel**.

* `echo "Bonjour Monde" > bonjour.txt` remplace le contenu du fichier `bonjour.txt` par le texte "Bonjour Monde".
* `echo "Bonjour Monde" >> bonjour.txt` ajoute le texte "Bonjour Monde" à la fin du fichier `bonjour.txt`.

## Environnement

### Paramétrage

L'apparence et les fonctionnalités de la ligne de commande Linux sont paramétrables. Les paramètres d'environnement de l'utilisateur sont regroupés dans le fichier `.bash_profile`, situé à la racine de son répertoire personnel.

### Variables d'environnement

Il est possible de définir des **variables d'environnement** pour stocker des informations globales ou modifier certains paramètres. Ces variables sont accessibles par tous les programmes.

Voici quelques-unes des variables d'environnement prédéfinies : 

* `USER` contient le nom de l'utilisateur courant.
* `HOME` contient le chemin du répertoire personnel de l'utilisateur courant.
* `PATH` contient une liste de chemins séparés par le caractère `:` et est utilisée pour trouver les commandes exécutables du système.

### Alias

Un alias permet de créer une nouvelle commande. On les utilise pour taper plus rapidement les commandes souvent utilisées, comme par exemple `ls -al`.

### Commandes à connaître

* `export` crée ou modifie la valeur d'une variable d'environnement.

    * `export MSG="Bienvenue"` crée une variable `MSG` ayant pour valeur "Bienvenue".

* `echo` peut afficher le contenu d'une variable d'environnement.

    * `echo $MSG` affiche le contenu de la variable `MSG`. Attention, le `$` est indispensable !

* `env` affiche la liste des variables d'environnement.

* `alias` définit un nouvel alias.

    * `alias ll="ls -l"` définit l'alias `ll` qui lancera la commande `ls -l`.

* `source ~/.bash_profile` permet d'activer les paramètres contenus dans le fichier `.bash_profile`.
