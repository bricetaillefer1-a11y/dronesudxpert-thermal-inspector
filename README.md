# Inspecteur Thermique — DroneSudXpert

Outil web interne pour analyser les photos prises par le drone (Matrice 4T et autres), en thermique comme en classique, et visualiser les orthophotos / modèles 3D générés par DJI Terra ou WebODM.

## Utiliser l'outil

Aucune installation nécessaire :

- **En local** : téléchargez `index.html` (bouton « Raw » puis enregistrer, ou « Download » sur GitHub) et ouvrez-le en double-cliquant dessus — ça s'ouvre directement dans votre navigateur. Une connexion internet est nécessaire au premier chargement pour les polices et bibliothèques utilisées (jsPDF, Three.js, GeoTIFF.js).
- **En ligne** : si l'hébergement GitHub Pages est activé sur ce dépôt (Settings → Pages), la même page est accessible via une adresse web fixe.

## Ce que fait l'outil aujourd'hui

**Onglet Analyse thermique**
- Import de plusieurs photos (glisser-déposer ou sélection), classiques ou thermiques DJI
- Visionneuse avec zoom/déplacement, lecture des métadonnées (date, GPS, altitude, appareil)
- Outils de mesure : point (intensité au survol) et zone rectangulaire (min/max/moyenne/% de points chauds)
- Seuil réglable + surimpression des points chauds
- Tableau récapitulatif du lot, export CSV et rapport PDF
- Panneau Diagnostic : structure JPEG brute + champs DJI détectés, utile pour identifier le format exact d'un fichier

**Onglet Orthophotos & Modèles 3D**
- Visionneuse d'orthophoto 2D (RGB et infrarouge séparément), formats JPG/PNG/WebP/TIFF, avec mode comparaison en rideau glissant
- Visionneuse de modèle 3D (RGB et infrarouge), formats .glb/.gltf ou .obj + .mtl + textures
- Ne génère aucune orthophoto/modèle 3D lui-même : ces fichiers doivent être produits avec DJI Terra ou WebODM, puis déposés ici pour consultation

## Important : mode « intensité relative »

Les valeurs affichées pour les photos thermiques sont aujourd'hui des **intensités relatives (0–255)**, pas des températures réelles en °C. Le décodage radiométrique exact des fichiers R-JPEG du Matrice 4T n'a pas encore pu être validé (DJI ne documente pas publiquement ce format, et il faut un fichier thermique **original**, non recompressé, pour le faire).

Pour activer le mode calibré : déposer dans l'outil un fichier `.JPG` thermique tel qu'il sort de la carte SD du drone (pas une capture d'écran, pas un fichier qui a transité par une messagerie — cela supprime les données nécessaires), puis demander à Claude de reprendre le décodage à partir du panneau Diagnostic.
