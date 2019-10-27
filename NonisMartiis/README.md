Nonis Martiis

En mars 2019, huit manuscrits (et non sept, finalement !) ont fait l'objet d'une segmentation manuelle (enluminures et tags) dans le cadre d'un stage d'un mois.
Ces données sont mises en ligne ici (et prochainement sur le site api.bnf.fr sous la licence ouverte etalab).

On propose trois formats de données : données brutes de l'application VGG Image Annotator (utilisée pour la segmentation), données ordonnées et enrichies des métadonnées de Mandragore au format CSV, annotations IIIF exploitables par le visualiseur Mirador.


*** Raw VIA Data ***

Pour chaque enluminure, appelée par l'URL de l'API IIIF Images de Gallica (comprenant son identifiant ark qualifié et ses coordonnées), on enregistre
- un seul attribut de fichier, correspondant à l'identifiant numérique de l'enluminure dans Mandragore (transformable en ark)
- et une série de "régions" correspondant chacune à un tag (occurrence d'un descripteur), avec pour chacun :
	* les coordonnées sur la reproduction de l'enluminure (déjà segmentée) du rectangle localisant le tag (x, y, width, height)
	* le libellé principal et le type du tag (objet, scène, personne, notion, lieu)
Attention, tous les tags ne sont pas localisés (certains ne sont pas localisables) et certaines enluminures ne sont associées à aucune région (parce qu'elles ne sont indexées par aucun tag, ou seulement par des tags non localisables).

On fournit également un fichier de modèle d'attributs permettant de poursuivre la segmentation dans VGG Image Annotator (version utilisée : 2.0.5).


*** Sorted Data ***

Ces données font l'objet d'un dictionnaire spécifique.
On se reportera également à la présentation et au dictionnaire des données du dump Mandragore, accessible sur http://api.bnf.fr/dumps-mandragore.


*** Mirador Annotations ***

Pour chacun des manuscrits segmentés, on fournit quatre fichiers d'annotations Mirador (inspirés du formalisme IIIF*).

L'affichage de ces annotations a été testée dans l'instance de Mirador développée en 2018 par la BnF pour le projet "Manuscrits médiévaux : France-Angleterre, 700-1200", accessible à l'adresse : https://manuscrits-france-angleterre.org/view3if/ (penser à ajouter le manifeste Gallica du document numérique, activer la fonction annotations et charger le fichier d'annotations)
- MiradorAnnotations_Enluminures.json contient seulement les enluminures : leur coordonnées affichables sur la page, une notice comprenant les métadonnées et le lien vers l'application web Mandragore, et tous les tags de Mandragore (non localisés)
- MiradorAnnotations_Descripteurs.json contient seulement les tags : leur coordonnées affichables sur la page, une notice comprenant les métadonnées du descripteur de Mandragore, et toutes les formes rejetées de Mandragore
- MiradorAnnotations_Mixed1.json, plus lisible, contient à la fois les enluminures (coordonnées et sujet) et leurs tags segmentés (coordonnées et libellé principal)
- MiradorAnnotations_Mixed2.json, plus complet, contient à la fois les enluminures (coordonnées et notice Mandragore) et leurs tags segmentés (coordonnées et notice du descripteur dans Mandragore)

Pour les fichiers "Mixed", on utilise le formalisme SVG pour afficher le contour des enluminures et tags de couleurs différentes.

Les fichiers JSON, structurés selon le formalisme adapté des spécifications de l'API IIIF Présentation*, intègrent des identifiants non affichés par Mirador. On a choisi d'identifier chaque enluminure par l'URL actionnable de sa notice dans Mandragore et chaque tag par l'URL de la notice de l'enluminure complété d'un qualificatif de granularité fictif. Actuellement ce qualificatif n'est pas pris en charge par l'application Mandragore.

* L'API IIIF Présentation 2.1.1 (https://iiif.io/api/presentation/2.1/) prescrit d'établir un fichier d'annotation par cannevas (par page), appelés dans le manifeste d'ensemble du document numérique. Le respecter strictement nécessite la mise en ligne d'un grand nombre de fichiers : on a préféré dans un premier temps le formalisme plus léger des fichiers d'annotation Mirador.
