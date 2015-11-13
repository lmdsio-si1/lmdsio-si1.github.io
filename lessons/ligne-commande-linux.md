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

### Commandes à connaître

* `pwd` (*print working directory*) affiche le chemin du répertoire courant.

* `ls` (*list*) affiche le contenu du répertoire courant.

* `cd` (*change directory*) permet de se déplacer dans le système de fichiers en changeant de répertoire courant.

    * Pour remonter d'un niveau dans l'arborescence, on utilise la commande `cd ..`
    * Pour revenir à la racine de l'arborescence, on utilise la commande `cd /`

### Chemin absolu, chemin relatif

L'emplacement de chaque ressource (fichier ou répertoire) dans le système de fichiers est appelé son **chemin**. Dans un chemin Linux, le séparateur dans entre deux répertoires est le caractère `/`.

On distingue deux types de chemins :

* Un chemin **absolu** identifie une ressource en commençant à la racine de l'arborescence, avec le caractère `/`. Un chemin absolu ne dépend pas du répertoire courant et est donc valide partout.

    * Exemples : `/home/baptiste/hello.txt`, `/etc/apache/httpd.conf` sont des chemins absolus.

* Un chemin **relatif** identifie une ressource à partir du répertoire courant. Il dépend donc du répertoire courant et n'est pas valide partout.

    * Exemples : `../marc/adresses.txt`, `documents/cours/si1.pdf` sont des chemins relatifs.

### Répertoire personnel

Sous Linux, chaque utilisateur (sauf `root`) dispose d'un répertoire personnel à son nom situé dans `/home`. Par exemple, le répertoire personnel de l'utilisateur `nicolas` est `/home/nicolas`.

Le chemin absolu du répertoire personnel peut s'écrire de manière abrégée avec le caractère `~` (*tilde*). Par exemple, le chemin `~/music/` pour l'utilisateur `nicolas` correspond au chemin absolu `/home/nicolas/music/`.

Pour revenir dans le répertoire personnel, on peut taper la commande `cd` sans rien d'autre.

## Modification

### Commandes à connaître

* `mkdir` (*make directory*) crée un nouveau répertoire dans le répertoire courant.

* `touch` crée un nouveau fichier (vide) dans le répertoire courant.

...