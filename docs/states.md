# FSM States

La fiche produit fonctionne sur le principe d'une machine à états très simplifiée (dans le sens ou toutes les transitions sont possibles). Les états sont simplement représentés sous la forme d'un objet contenant la liste des différents états possibles. Dans le cas de la fiche produit, ces états sont standardisés et sont spécifiés dans le fichier `content.json > productSheets[] > states` des différentes variantes de configurations fournies par l'API PHP de test `public/api`. <span class="badge">ce point est amené à changer selon l'implémentation de l'API en production</span>

Les états présents dans `content.json` (fournis par l'API) sont fusionnés avec les états de base de la fiche produit et inséré dans l'état `FSMStates.dynamicStates`. Ce sont ces données qu'il faut utiliser avec l'outil maxscript.
![](https://github.com/Tribia3d/skaleone.doc/assets/40400644/aa4aeac5-53b2-456d-9cce-beb70fc7f1aa)

Le fichier `sharedFSMStates.js` est celui utilisé par l'outil maxscript, et ce sont ces états qu'il faut spécifier pour un bon fonctionnement de la fiche produit.
