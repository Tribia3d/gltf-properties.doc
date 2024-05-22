# Outil maxscript GTLF Properties

<style>img {float:right;margin:1rem;}
h1, h2, h3, h4, h5, h6 { clear:both;}
</style>

L'outil maxscript `GLTF Properties` permet de configurer les objets dans 3ds Max afin de leur ajouter des propriétés interprétables par la fiche produit **Skale One**.
Dans les grandes lignes, cela permet de spécifier le(s) type(s) et les paramètres des objets sélectionnés, afin de pouvoir intéragir avec eux dans la fiche produit.

## Installation
### Copie des fichiers
Il faut simplement copier le contenu de l'archive `maxscript-webgl-properties.zip` de l'outil maxscript dans le répertoire `/scripts` du dossier d'installation de 3ds Max (par défaut: `C:\Program Files\Autodesk\3ds Max 202x\scripts\`).

### Création du bouton dans 3ds Max
![](https://github.com/Tribia3d/gltf-properties.doc/assets/40400644/76811d0c-9a09-4801-b535-a74d2c232e8b)
L'outil étant un `macroscript`, il est nécessaire de lui attribuer un raccourci ou bien créer un bouton dans une toolbar.
Il se trouve dans la catégorie `TRIBIA`.

## Fonctionnement
Les objets sélectionnés sont affichés dans la liste en haut. Il est possible de les éditer un par un ou plusieurs à la fois.
Lorsque des modifications sont faites, le nom de l'objet apparait en gras dans la liste. Les modifications ne sont pas enregistrées dans la scène (et seront perdues en cas de fermeture de l'outil), tant que le bouton `Enregistrer Sélection` n'auta pas été cliqué.
```note
Lorsque l'outil est ouvert et que de nouveaux objets sont créés dans la scène, il se peut qu'il y ait des problèmes de nom (notamment pour les caméras). Dans ce cas il suffit de recharger l'outil avec le bouton `Reload`.
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
