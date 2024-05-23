# FSM States

La fiche produit fonctionne sur le principe d'une machine à états très simplifiée (dans le sens ou toutes les transitions sont possibles). Les états sont simplement représentés sous la forme d'un objet contenant la liste des différents états possibles. Dans le cas de la fiche produit, ces états sont standardisés et sont spécifiés dans le fichier `content.json > productSheets[] > states` des différentes variantes de configurations fournies par l'API PHP de test `public/api`. <span class="badge"ce point est amené à changer selon l'implémentation de l'API en production</span>
