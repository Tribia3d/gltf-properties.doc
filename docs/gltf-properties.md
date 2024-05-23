# Outil maxscript GTLF Properties

<style>
  img {float:right;margin:1rem;}
  .inline img {}
  h1, h2, h3 /*, h4, h5, h6 */ { clear:both;}
</style>

L'outil maxscript `GLTF Properties` permet de configurer les objets dans 3ds Max afin de leur ajouter des propriétés interprétables par la fiche produit **Skale One**.
Dans les grandes lignes, cela permet de spécifier le(s) type(s) et les paramètres des objets sélectionnés, afin de pouvoir intéragir avec eux dans la fiche produit.

<span class="space"/>
## Installation

### Copie des fichiers
Il faut simplement copier le contenu de l'archive `maxscript-webgl-properties.zip` de l'outil maxscript dans le répertoire `/scripts` du dossier d'installation de 3ds Max (par défaut: `C:\Program Files\Autodesk\3ds Max 202x\scripts\`).

### Création du bouton dans 3ds Max
![customize interface](https://github.com/Tribia3d/skaleone.doc/assets/40400644/3f7cecb5-5bd4-4f4c-bd30-afd0daa58f39)
L'outil étant un `macroscript`, il est nécessaire de lui attribuer un raccourci ou bien créer un bouton dans une toolbar.
Il se trouve dans la catégorie `TRIBIA`.

<span class="space"/>
## Fonctionnement & prise en main
Les objets sélectionnés sont affichés dans la liste en haut. Il est possible de les éditer un par un ou plusieurs à la fois.
Lorsque des modifications sont faites, le nom de l'objet apparait en gras dans la liste. Les modifications ne sont pas enregistrées dans la scène (et seront perdues en cas de fermeture de l'outil), tant que le bouton `Enregistrer Sélection` n'aura pas été cliqué.

![outil](https://github.com/Tribia3d/skaleone.doc/assets/40400644/ddb55d2c-e8ca-4945-ae3d-c6fcd2f3327f)
Lorsque plusieurs objets sont sélectionnés dans la liste ayant des propriétés dont la valeur est identique, ces valeurs sont affichées normalement. Si les valeurs sont différentes, un tiret `—` (ou un carré dans le cas des cases à cocher) est affiché. Si aucune modification n'est apportée dans le champ en question, les valeurs de chacun des objets resteront telles quelles. Par contre, le fait de modifier une valeur avant plusieurs objets sélectionnés va écraser les différentes valeurs de chacun. En cas d'erreur il suffit de cliquer sur le bouton `Recharger` _sans enregistrer_.

Le bouton `Enregistrer Tout` va quant à lui enregistrer les modifications sur **tous** les objets de la scène, et pas simplement ceux sélectionnés. Un message de confirmation est affiché avant l'enregistrement.

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
## Propriétés Générales
![general](https://github.com/Tribia3d/skaleone.doc/assets/40400644/e5304234-e174-493c-869b-85e717a5c000)
Il s'agit des propriétés de base qui ne dépendent pas du (des) type(s) appliqué(s). En bas se trouve l'aperçu de la configuration au format JSON (en lecture seule).

- [**Type**](#types) : liste permettant d'appliquer un (ou plusieurs) type(s) aux objets, leur ajoutant des fonctions au sein de la fiche produit.
- **Active States** : liste des [états de l'application](states.md) dans lesquels l'objet sera affiché (ou actif dans le cas des caméras). _(Les `annotations` possèdent leur propre champ Annotation Active States dédié.)_
  - **Invert States** : inverse l'effet du champ précédent. L'objet sera affiche dans les états non présents dans la liste `Active States`.
- **Cast Shadows When Invisible** <span class="badge">non utilisé</span> : lorsque l'objet est masqué (en raison du champ `Active States`) son ombre reste appliquée sur les autres objets.
- **Note** : bloc de texte qui n'a pas d'impact sur la scène permettant de noter des informations diverses si besoin.


<span class="space"/>
## Types

- [camera_virtual & camera_virtual_target](#camera_virtual--camera_virtual_target)
- [annotation](#annotation)
- [gotoState](#gotostate)
- [billboard](#billboard)
- [shadow_plane_height](#shadow_plane_height)

<span class="space"/>
### camera_virtual & camera_virtual_target
![camera_virtual](https://github.com/Tribia3d/skaleone.doc/assets/40400644/4f1c6b4d-1241-43fe-8de4-ca64803da2ad)
La fiche produit fonctionne grâce à un système de caméras virtuelles. La caméra utilisée pour le rendu est toujours la même, mais sa position et ses propriétés sont calquées sur différentes caméras virtuelles. Lors d'un changement d'état, la caméra virtuelle _active_ vera ses paramètres recopiés sur la caméra principale.

Le plus simple est d'utiliser une `Physical Camera` de 3ds Max avec une cible. On appliquera le type `camera_virtual` à la caméra et le type `camera_virtual_target` à la cible (autrement la cible ne sera pas exportée en gltf).

Concernant la cible, il faut simplement lui spécifier le type `camera_virtual_target`, il n'y a pas d'autres paramètres.

#### Paramètres
- **Camera Target** <span class="badge">requis</span> : spécifie la cible de la caméra. Permettra d'orienter la caméra dans la fiche produit. Lors de l'export il n'y a plus de lien entre la caméra et l'objet cible, ce champ est donc nécessaire.
- **Lerp duration** : durée de l'interpolation entre les positions et orientations des caméras lors la transition d'état.
- **Orbit Controls** : détermine si la caméra est contrôlable ou figée.
- **Enable Rotate** : active ou non la possibilité de faire tourner la caméra.
- **Enable Pan** : active ou non la possibilité de déplacer latéralement la caméra.
- **Enable Zoom** : active ou non la possibilité de zoomer (dolly : changement de la distance de la caméra à la cible).
- **Min Azimuth Angle** <span class="badge">non utilisé</span> : rotation minimale sur le plan horizontal, valeur comprise dans l'intervalle `[-2 PI, 2 PI]`.
- **Max Azimuth Angle** <span class="badge">non utilisé</span> : rotation maximale sur le plan horizontal, valeur comprise dans l'intervalle `[-2 PI, 2 PI]`.
- **Min Polar Angle** <span class="badge">non utilisé</span> : rotation minimale sur le plan vertical, vaeur comprise dans l'intervalle `[0, PI]`.
- **Max Polar Angle** <span class="badge">non utilisé</span> : rotation maximale sur le plan vertical, vaeur comprise dans l'intervalle `[0, PI]`.
- **Min Distance** : distance minimale à laquelle il est possible de s'approcher
- **Max Distance** : distance maximale à laquelle il est possible de s'éloigner
- **Ground Threshold** : si spécifiée, cette valeur va bloquer la rotation de la caméra au niveau du seuil indiqué (en mètres) par rapport au sol (`z = 0` dans 3ds Max ou `y = 0` en webgl)
- **Auto Rotate** : active ou non la rotation automatique autour de la cible.

```warning
En cas de duplication d'une caméra pendant que l'outil est ouvert il sera nécessaire de recharger l'outil (fermer et réouvrir l'outil ou bien cliquer sur le bouton `Reload` en haut) autrement le nom de la cible sera incorrect et la fiche produit ne pourra pas retrouver le bon objet.
```

```warning
Il est possible que suite à une erreur de saisie plus d'une caméra soit active dans un état donné (états actifs similaire entre plusieurs caméras). Dans ce cas la caméra réellement utilisée est imprévisible, ce cas de figure est à proscrire !
```

<span class="space"/>
### annotation
![annotation](https://github.com/Tribia3d/skaleone.doc/assets/40400644/2eb31636-53d2-4d27-9a44-e1c2d2d859f9)
Les annotations sont des puces et des tooltips affichés sur un calque 2d rattachés à des objets dans la scène 3d. Lorsque la caméra ou les objets bougent, les annotations 2d suivent le mouvement.

#### Paramètres
- **Annotation Id** : référence de l'annotation dans le fichier de configuration JSON. Permet de faire correspondre l'objet avec son contenu.
- **Annotation Style** <span class="badge">non utilisé</span> : permet de choisir le style de l'annotation. Pour l'instant la fiche produit ne possède qu'un seul style, ce paramètre n'est donc pas utilisé, et sera sans doute déplacé dans le fichier de configuration par la suite.
- **Annotation Active States** : liste des [états](states.md) dans lesquels l'annotation sera visible.
  - **Annotation Invert States** : inverse l'effet du champ `Annotation Active States`.
- **Annotation Outline Selected** : affiche ou non un contour sur cet objet et ses descendants hiérarchiques lors du survol de la souris.
- **Annotation Force Position** : permet de forcer la position du tooltip par rapport à la puce. Par défaut le tooltip est placé au dessus de la puce.

<span class="space"/>
### gotoState
![gotoState](https://github.com/Tribia3d/skaleone.doc/assets/40400644/82966304-bb35-47c1-9e7e-e2d43633979d)
Permet de changer d'[état](states.md) lors du clic sur un objet ou l'annotation (puce / tooltip).

#### Paramètre
- **Goto State** : state vers lequel transitionner lors du clic.

<span class="space"/>
### billboard
![orientation pivot billboard](https://github.com/Tribia3d/skaleone.doc/assets/40400644/5911d9d9-9946-4297-9ce4-20c8452223e1)
Les objets ayant le type `billboard` sont automatiquement orienté en direction de la camera.
Il faut prendre garde à modifier le pivot de l'objet en question afin que l'axe Y (3ds Max) "entre" dans l'objet.

<span class="space"/>
### shadow_plane_height
Les ombres (contact ou dynamiques) sont projetées sur un plan horizontal. Ce paramètre permet de déterminer la hauteur (z dans 3ds Max et y en webgl) de ce plan via la position de l'objet sur lequel il est appliqué.
Il n'y a aucune paramètre particulier, il faut simplement spécifier le type `shadow_plane_height` à un objet.
