

# Live-LFI & RFI

## Objectif
Le challenge consiste à exploiter une vulnérabilité de Local File Inclusion (LFI) et Remote File Inclusion sur le site https://lfi.warchall.net/ et https://rfi.warchall.net/. L'objectif est de lire le contenu du fichier `solution.php` sur https://lfi.warchall.net/index.php?lang=solution.php et https://rfi.warchall.net/index.php?lang=solution.php pour récupérer le flag.

## Procédure d'exploitation

1. **PHP Warper ou Data Stream**
   - Cette fois, j'ai résolu deux des séries Live de WeChall pour pratiquer les techniques LFI et RFI en utilisant PHP Wrapper ou Data Stream


2. **LFI**
   
   - Dans le cas de Warchall : Live LFI, vous pouvez utiliser PHP Wrapper pour accéder au fichier en utilisant ```php://filter/convert.base64-encode/resource=solution.php```

3. **RFI**
   - Dans le cas de Warchall : Live RFI, vous pouvez utiliser Data Stream pour accéder au fichier en utilisant ```data://text/plain,<?php echo `cat solution.php`; ?>```

4. **Contenu de solution.php**
   - Le fichier `solution.php` contient le flag recherché
     - Pour LFI, decodez le contenu encodé en Base64
     - Pour RFI, voir le code source
