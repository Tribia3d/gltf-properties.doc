# Outil maxscript GTLF Properties

<style>
  img {float:right;margin:1rem;}
  .inline img {}
  h1, h2, h3, h4, h5, h6 { clear:both;}
</style>

L'outil maxscript `GLTF Properties` permet de configurer les objets dans 3ds Max afin de leur ajouter des propriétés interprétables par la fiche produit **Skale One**.
Dans les grandes lignes, cela permet de spécifier le(s) type(s) et les paramètres des objets sélectionnés, afin de pouvoir intéragir avec eux dans la fiche produit.


<span class="space"/>
## Installation

### Copie des fichiers
Il faut simplement copier le contenu de l'archive `maxscript-webgl-properties.zip` de l'outil maxscript dans le répertoire `/scripts` du dossier d'installation de 3ds Max (par défaut: `C:\Program Files\Autodesk\3ds Max 202x\scripts\`).

### Création du bouton dans 3ds Max
![](https://github.com/Tribia3d/skaleone.doc/assets/40400644/3f7cecb5-5bd4-4f4c-bd30-afd0daa58f39)
L'outil étant un `macroscript`, il est nécessaire de lui attribuer un raccourci ou bien créer un bouton dans une toolbar.
Il se trouve dans la catégorie `TRIBIA`.


<span class="space"/>
## Fonctionnement & prise en main
Les objets sélectionnés sont affichés dans la liste en haut. Il est possible de les éditer un par un ou plusieurs à la fois.
Lorsque des modifications sont faites, le nom de l'objet apparait en gras dans la liste. Les modifications ne sont pas enregistrées dans la scène (et seront perdues en cas de fermeture de l'outil), tant que le bouton `Enregistrer Sélection` n'auta pas été cliqué.

![](https://github.com/Tribia3d/skaleone.doc/assets/40400644/ddb55d2c-e8ca-4945-ae3d-c6fcd2f3327f)
Lorsque plusieurs objets sont sélectionnés dans la liste ayant des propriétés dont la valeur est identique, ces valeurs sont affichées normalement. Si les valeurs sont différentes, un tiret `—` (ou un carré dans le cas des cases à cocher) est affiché. Si aucune modification n'est apportée dans le champ en question, les valeurs de chacun des objets resteront telles quelles. Par contre, le fait de modifier une valeur avant plusieurs objets sélectionnés va écraser les différentes valeurs de chacun. En cas d'erreur il suffit de recharger l'outil _sans enregistrer_.

```note
Lorsque l'outil est ouvert et que de nouveaux objets sont créés dans la scène, il se peut qu'il y ait des problèmes de nom (notamment pour les caméras). Dans ce cas il suffit de recharger l'outil avec le bouton `Reload` (mais attention aux modifications non enregistrées).
```

```note
Pour certains champs, il est possible de créer des valeurs si elles n'existent pas dans la liste. Pour cela il suffira d'écrire la nouvelle valeur et recliquer sur `Create "abcd"`. La nouvelle valeur apparaitra alors sur fond rouge dans les champs à choix multiples.
```

```note
La manière dont 3ds Max gère la fenêtre empêche d'utiliser les raccourcis clavier, il n'est donc pas possible d'utiliser `CTRL + C` et `CTRL + V` pour copier / coller du texte. Mais cela fonctionne avec le menu contextuel de la soucis (clic droit).
```


<span class="space"/>
## Propriétés `Générales
![](https://github.com/Tribia3d/skaleone.doc/assets/40400644/e5304234-e174-493c-869b-85e717a5c000)
Il s'agit des propriétés qui ne dépendent pas du (des) type(s) appliqué(s). On y retrouve le choix du type, les états actifs de l'objet, un champ pour ajouter des notes. Et en bas le JSON de la configuration (en lecture seule).

- [**Type**](#types-des-objets) : Liste permettant d'appliquer un (ou plusieurs) type(s) aux objets, leur ajoutant des fonctions au sein de la fiche produit.
- [**Active States**](#active-states) : Liste des états de l'application dans lesquels l'objet sera affiché (ou actif dans le cas des caméras)
  - **Invert States** : inverse l'effet du champ précédent. L'objet sera affiche dans les états non présents dans la liste `Active States`.
- **Cast Shadows When Invisible** <span class="badge">non utilisé</span> : Lorsque l'objet est masqué (en raison du champ `Active States`) son ombre reste appliquée sur les autres objets.
- **Note** : Bloc de texte qui n'a pas d'impact sur la scène permettant de noter des informations diverses si besoin.


<span class="space"/>
## Types

- camera_virtual
- camera_virtual_target
- annotation
- gotoState

### `camera_virtual`
La fiche produit fonctionne grâce à un système de caméras virtuelles. La caméra utilisée pour le rendu est toujours la même, mais sa position et ses propriétés sont calquées sur différentes caméras virtuelles. Lors d'un changement d'état, la caméra virtuelle _active_ vera ses paramètres reocpiés sur la caméra principale.

```warning
Il est possible que suite à une erreur de saisie plus d'une caméra soit active dans un état donné. Dans ce cas la caméra réellement utilisée est imprévisible, ce cas de figure est à proscrire !
```

### `camera_virtual_target`
### `annotation`
### `gotoState`
