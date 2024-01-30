# **Py-Tong**

Ce script Python prend un chemin de fichier en argument en ligne de commande, lit son contenu, effectue des vérifications, et imprime des messages en fonction du résultat. Si la solution est correcte, le script affiche le contenu d'un fichier spécifié par la variable `SOLUTION` (`/home/level/12/solution.txt`).

## Objectif du Challenge

L'objectif de ce challenge est de détecter la vulnérabilité dans le code Python fourni, permettant d'imprimer le contenu du fichier spécifié par `SOLUTION` (`/home/level/12/solution.txt`).

## Fonctionnement du Script

1. **Vérifications préliminaires**:
    - Le script vérifie si le chemin du fichier contient certains motifs ("proc", "uptime", "tmp", "random", "full", "zero", "null"). En cas de correspondance, une exception (`ValueError`) est levée avec le message "nononono: hacking is not allowed".
    - Il vérifie également si le fichier spécifié existe. En cas d'absence, une exception est levée avec le message "sorry file "%s" does not exist" % filepath.

2. **Lecture du fichier initial**:
    - Le script ouvre le fichier spécifié, lit son contenu, et le stocke dans la variable `jjk`.

3. **Vérification du fichier après la lecture initiale**:
    - Si le fichier n'existe plus après la première lecture, le script imprime "You are l33t" et retourne `True`.

4. **Re-lecture du fichier**:
    - Si le fichier existe toujours, le script le rouvre, lit son contenu, et le stocke dans la variable `kwisatz`.

5. **Comparaison des contenus**:
    - Il compare les contenus initiaux (`jjk`) et actuels (`kwisatz`). En cas de différence, le script imprime "You are a winner" et retourne `True`.

6. **Cas par défaut**:
    - Si aucune des conditions ci-dessus n'est satisfaite, le script lance une exception avec le message "fail...".

7. **Exécution principale**:
    - Dans la partie `__main__`, le script vérifie si le nombre d'arguments en ligne de commande est suffisant. En cas de défaut, il imprime "wrong argcount" et quitte le script avec le code de sortie 1.
    - Il appelle la fonction `main` avec le chemin du fichier spécifié et capture toute exception qui pourrait être levée.
    - En l'absence d'exception, le script imprime le contenu du fichier défini par `SOLUTION` (`/home/level/12/solution.txt`).

## Solution

Le script utilise un fichier temporaire en tant qu'argument. Lorsque ce fichier temporaire est supprimé, le script imprime le contenu du fichier défini par `SOLUTION` (`/home/level/12_pytong/solution.txt`).

Pour tester le script, placez-vous dans le répertoire `/home/level/12_pytong/` et exécutez la commande suivante dans le terminal bash :

```bash
./pytong <(echo aaa)
```

Cette commande utilise la substitution de processus `<(...)` pour créer un fichier temporaire contenant le texte "aaa". Ensuite, elle utilise ce fichier temporaire comme argument pour le script `pytong`. Après l'exécution, le script imprime le contenu du fichier défini par `SOLUTION`.