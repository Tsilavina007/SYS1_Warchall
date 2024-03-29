
# **Training: Warchall - The Beginning**

## Objectif
L'objectif de ce premier chapitre est de trouver les 6 drapeaux sur le serveur warchall.net .



### Connection SSH

 - Créez un compte SSH dans le site [Wechall](https://www.wechall.net/challenge/warchall/begins/index.php) et connectez-vous au serveur en utilisant le mot de passe du formulaire, en utilisant Putty ou un terminal
   ```bash
   ssh -p 19198 your_username@server_address
   ```
## Level00

- **Étape 1 :** À l'intérieur du serveur, utilisez la commande `ls` pour voir le contenu du répertoire actuel.
   ```bash
   ls
   ```

- **Étape 2 :** Le mot de passe se trouve dans le fichier "WELCOME.md".
   ```bash
   cat WELCOME.md
   ```

## Level01

- **Étape 1 :** Accédez à /home/level avec la commande `cd`.
   ```bash
   cd /home/level
   ```

- **Étape 2 :** Utilisez `ls` pour voir les fichiers et répertoires à cet emplacement.
   ```bash
   ls
   ```

- **Étape 3 :** Allez dans /01_choice_tree.
   ```bash
   cd /01_choice_tree
   ```

- **Étape 4 :** Ignorez le contenu de README.md et allez dans le répertoire spécifié où le drapeau est dans le fichier SOLUTION.txt.
   ```bash
   cd blue/hats/grey/solution/patience
   cat SOLUTION.txt
   ```

## Level02

- **Étape 1 :** Retournez à /home/level et allez dans /02.
   ```bash
   cd /home/level/02
   ```

- **Étape 2 :** Utilisez la commande `ls -al` pour voir les fichiers cachés.
   ```bash
   ls -al
   ```

- **Étape 3 :** Allez dans /.porb, le mot de passe pour ce drapeau est dans .solution.
   ```bash
   cd /.porb
   cat .solution
   ```

## Level03

- **Étape 1 :** Retournez à /home/level et allez dans /03.
   ```bash
   cd /home/level/03
   ```

- **Étape 2 :** Tous les contenus de /03 sont cachés, utilisez `ls -al` pour les voir.
   ```bash
   ls -al
   ```

- **Étape 3 :** Le mot de passe pour ce drapeau est dans .bash_history. Utilisez `cat` pour voir le contenu.
   ```bash
   cat .bash_history
   ```

## Level04

- **Étape 1 :** Allez dans /home/user/YourUsername/level/04_kwisatz.
   ```bash
   cd /home/user/YourUsername/level/04_kwisatz
   ```

- **Étape 2 :** Il y a deux fichiers README.txt et README2.md.
- **Étape 3 :** Le mot de passe est dans README2.md. Utilisez `chmod` pour accorder les permissions et `cat` pour voir le contenu.
   ```bash
   chmod ugo+r README2.md
   cat README2.md
   ```

## Level05

- **Étape 1 :** Allez dans home/level/05_privacy/.
   ```bash
   cd home/level/05_privacy
   ```

- **Étape 2 :** La solution se trouve dans le fichier README.md.
   ```bash
   cat README.md
   ```