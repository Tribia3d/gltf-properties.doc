# Outil maxscript GTLF Properties

<style>
  img {float:right;margin:1rem;}
  .inline img {}
  h1, h2, h3, h4, h5, h6 { clear:both;}
</style>

L'outil maxscript `GLTF Properties` permet de configurer les objets dans 3ds Max afin de leur ajouter des propriétés interprétables par la fiche produit **Skale One**.
Dans les grandes lignes, cela permet de spécifier le(s) type(s) et les paramètres des objets sélectionnés, afin de pouvoir intéragir avec eux dans la fiche produit.

## Installation
### Copie des fichiers
Il faut simplement copier le contenu de l'archive `maxscript-webgl-properties.zip` de l'outil maxscript dans le répertoire `/scripts` du dossier d'installation de 3ds Max (par défaut: `C:\Program Files\Autodesk\3ds Max 202x\scripts\`).

### Création du bouton dans 3ds Max
![](https://github.com/Tribia3d/skaleone.doc/assets/40400644/3f7cecb5-5bd4-4f4c-bd30-afd0daa58f39)
L'outil étant un `macroscript`, il est nécessaire de lui attribuer un raccourci ou bien créer un bouton dans une toolbar.
Il se trouve dans la catégorie `TRIBIA`.

## Fonctionnement & prise en main
Les objets sélectionnés sont affichés dans la liste en haut. Il est possible de les éditer un par un ou plusieurs à la fois.
Lorsque des modifications sont faites, le nom de l'objet apparait en gras dans la liste. Les modifications ne sont pas enregistrées dans la scène (et seront perdues en cas de fermeture de l'outil), tant que le bouton `Enregistrer Sélection` n'auta pas été cliqué.

![](https://github.com/Tribia3d/skaleone.doc/assets/40400644/ddb55d2c-e8ca-4945-ae3d-c6fcd2f3327f)
Lorsque plusieurs objets sont sélectionnés dans la liste ayant des propriétés dont la valeur est identique, ces valeurs sont affichées normalement. Si les valeurs sont différentes, un tiret `—` (ou un carré dans le cas des cases à cocher) est affiché. Si aucune modification n'est apportée dans le champ en question, les valeurs de chacun des objets resteront telles quelles. Par contre, le fait de modifier une valeur avant plusieurs objets sélectionnés va écraser les différentes valeurs de chacun. En cas d'erreur il suffit de recharger l'outil _sans enregistrer_.

```note
Lorsque l'outil est ouvert et que de nouveaux objets sont créés dans la scène, il se peut qu'il y ait des problèmes de nom (notamment pour les caméras). Dans ce cas il suffit de recharger l'outil avec le bouton `Reload` (mais attention aux modifications non enregistrées).
```

```note
La manière dont 3ds Max gère la fenêtre empêche d'utiliser les raccourcis clavier, il n'est donc pas possible d'utiliser `CTRL + C` et `CTRL + V` pour copier / coller du texte. Mais cela fonctionne avec le menu contextuel de la soucis (clic droit).
```

## Propriétés `Générales

## `Types` des objets

- camera_virtual
- camera_virtual_target
- annotation
- gotoState
