# **Choose Your Path**

## Objectif
Le challenge consiste à lire le contenu du fichier solution.txt en exploitant une vulnérabilité dans le programme charp.c.

## Fonctionnement du Script

Le script charp.c prend en entrée un nom de fichier et utilise la fonction `popen` pour exécuter les commandes système `wc -l` et `wc -c` sur ce fichier. Cependant, une vulnérabilité réside dans la manière dont le nom de fichier est manipulé, permettant potentiellement l'injection de commandes.

## Vulnérabilité
Le programme charp.c utilise la fonction `popen` pour exécuter des commandes système basées sur l'entrée de l'utilisateur, créant ainsi une vulnérabilité.


## Solution
La solution implique l'injection d'une commande à travers l'argument du programme charp.c. Utilisez le caractère `"&"` pour exécuter plusieurs commandes en une seule. 

Pour tester le script, placez-vous dans le répertoire `/home/level/10_choose_your_path/` et exécutez la commande suivante dans le terminal bash :

```bash
./charp "tsong & cat solution.txt > ~/solution_l10"
```
>Les contenus de solution.txt y compris le flag seront dans le fichier solution_l10 de votre repertoire personnel.
