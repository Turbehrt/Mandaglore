# Thésaurus iconographique Mandragore 

La base iconographique Mandragore utilise un thésaurus iconographique de référence de plus de 20 000 mots-clés utilisés pour l’indexation des enluminures. Il s’agit pour l’essentiel de noms communs (objets, bâtiments… visibles sur l’image), traduits en anglais, allemand, italien et espagnol, mais également de noms de personnes, de lieux, ou de notions plus abstraites (« allégorie »…). 

Ce thésaurus est consultable en ligne sur le site [https://mandragore.bnf.fr/](https://mandragore.bnf.fr/) (en passant par l’exploration des mots-clés), où il est mis à jour de façon continue en fonction des besoins d’indexation. Le présent jeu de données en fait l’extraction régulière pour permettre de le télécharger au format XML/SKOS. 

## Historique 

La base iconographique Mandragore a été conçue en 1989. Elle utilisait initialement un vocabulaire d’indexation adapté du Thésaurus iconographique de François Garnier, dont l’usage était largement promu au sein des institutions du ministère de la culture. 

Pour des raisons techniques, il avait cependant été procédé à une simplification effaçant la hiérarchie du thésaurus Garnier. Les mots-clés utilisés pour l’indexation, appelés « descripteurs », étaient classés en adaptant la classification Dewey, chaque mot-clé pouvant être classé dans plusieurs classes. Cette organisation visait à faciliter la découverte du vocabulaire, mais n’était pas utilisée pour la recherche. 

Au fur et à mesure des enrichissements de Mandragore et de l’apparition de nouveaux besoins, le vocabulaire a été complété, dépassant le cadre initial du thésaurus Garnier. Une attention a été portée à la cohérence des nouveaux ajouts, mais sans alignement sur un référentiel externe. En particulier, la politique d’indexation de Mandragore consiste à identifier le plus précisément possible les éléments visibles sur l’image, en privilégiant le spécifique au générique, même lorsque l’intention de l’enlumineur ne peut être précisément établie. Ainsi, un poisson ne sera indexé comme « poisson » que lorsqu’il n’est pas possible d’en déterminer l’espèce (selon les connaissances actuelles), et de préférence comme « ablette », « églefin » ou « sardine ». Pour faciliter la lecture et la recherche, certains mots-clés disposent d’une définition et parfois d’une note explicative (voir le modèle de données ci-dessous). 

À l’occasion de la refonte de Mandragore (2020-2022), le thésaurus a été mis en conformité avec la norme ISO 25964-1. En particulier, on opère désormais une distinction entre concept et termes, et des relations hiérarchiques ou associatives entre concepts sont possibles. Autant que possible, des liens sont proposés avec les fichiers d’autorités de la BnF (personnes, lieux, matière). Une reprise de données minimale a été menée : on a notamment retiré les signes parasites (points à la place des espaces) et inséré des majuscules aux noms propres (et noms communs allemands). La langue des traductions a également été formalisée, mais celles-ci n’ont pas été systématiquement dédoublées pour l’instant (par exemple le mot-clé « verveine » ne dispose que d’une forme « verbena », homonyme en espagnol et en italien). 

Une révision plus générale (création de termes génériques et d’associations, révision des formes de référence…) interviendra progressivement dans les années à venir. 

## Modèle de données 

Le présent jeu de données est mis à disposition au format XML/SKOS. 

Chaque mot-clé est un concept (au sens de la norme ISO) disposant d’un identifiant unique. Il est associé à au moins un terme de préférentiel en français (ou forme internationale de référence pour les noms propres), et peut être associé à un ou plusieurs termes non-préférentiels en français, anglais, allemand, italien ou espagnol. 

Chaque terme peut être associé à une définition, généralement un terme générique (« églefin, définition : poisson ») ou une désambiguïsation (date de fête pour les noms de saints, domaine d’application, localisation…). 

Chaque mot-clé peut également disposer d’une note explicative (complément d’identification, référence bibliographique…) en français, applicable à l’ensemble des termes. Autant que possible, il est associé à une entité de l’un des fichiers d’autorités de la Bibliothèque nationale de France, identifié par son identifiant ARK. Ces alignements ont pour l’essentiel été réalisés dans le cadre du projet Biblissima (voir ci-dessous). 

Chaque mot-clé relève d’au moins un groupe de concepts, issus de la classification Dewey (sans indice) et hiérarchisés. 

Enfin chaque mot-clé peut être associé à un ou plusieurs autres mots-clés par des relations hiérarchiques ou associatives (« voir aussi », « ne pas confondre »…). 

Les concepts génériques (« amphibien », « poisson », « instrument de musique ») ne sont pas directement utilisés en indexation ; ils jouent un rôle de regroupement pour des concepts plus spécifiques. Pour éviter toute confusion, leur terme préférentiel est entre parenthèses, et associé à la définition « terme générique ». L'utilisation de relations hiérarchiques reste rare dans le thésaurus Mandragore, qui ne comprend pas de « top concepts » au sens de SKOS.

## Identifiants 

Les groupes de concepts, concepts et termes sont dotés d’un identifiant alphanumérique unique. 

Pour l’instant, cet identifiant n’est pas un identifiant pérenne de type ARK : la BnF ne s’engage donc pas sur la pérennité de ces identifiants. 

Néanmoins, les numéros de descripteurs utilisés dans le précédent site Mandragore (2003-2022) ont été maintenus, mais préfixés de la chaîne de caractère « mdgc ». 

Ainsi l’ancien descripteur « dragon », dont la notice était accessible à l’adresse http://mandragore.bnf.fr/jsp/afficherNoticeDesc.jsp?id=165 est devenu le concept mdgc165 (terme préférentiel : « dragon »), dont la notice est accessible à l’adresse https://mandragore.bnf.fr/mdgc165. 

Seuls les identifiants de concepts (mots-clés) sont actionnables sous forme d’URL. Les identifiants des groupes de concepts et des termes ne sont actuellement pas affichés sur le site Mandragore. (Les identifiants des termes ne sont pas inclus dans le présent export, qui n'utilise pas l'extension skos-xl.

## Mise à jour des données

Le présent export utilise les données migrées entre août et novembre 2022. Il n'intègre pas l'historique des mises à jour antérieures, non documentées dans l'ancienne application Mandragore.

De futures versions de cet export seront amenées à intégrer les mises à jour du thésaurus réalisées depuis novembre 2022. En 2024, date de cet export, ces modifications restent très limitées.

## Expérimentations sur le thésaurus Mandragore

### STITCH 

Entre 2006 et 2009, le projet STITCH (Semantic Interoperability to Access Cultural Heritage) a expérimenté l’alignement semi-automatique du vocabulaire iconographique de Mandragore (ancienne version) avec la classification Iconclass mise en œuvre par la bibliothèque nationale des Pays-Bas pour la description de ses enluminures. 

Un prototype permettant l’exploration d’un échantillon d’enluminures avait été mis en place (mais n’est plus maintenu). Les fichiers produits dans le cadre de cette expérimentation sont disponibles sur demande. 

Ce projet a permis l’expérimentation du format XML/SKOS (officiellement publié en 2009). 

Plus d’information sur le projet STITCH sur le [site des projets de recherche de la BnF](https://actions-recherche.bnf.fr/bnf/anirw3.nsf/IX01/A2014000409_stitch-semantic-interoperability-to-access-cultural-heritage). 

### Biblissima 

Dans le cadre du premier Equipex Biblissima (2012-2021), un important travail d’alignement des vocabulaires iconographiques de Mandragore (ancienne version) et Initiale (base des enluminures des manuscrits des bibliothèques publiques de France, maintenue par l’Institut de Recherche et d’Histoire des Textes du CNRS). 

Un prototype d’interrogation croisée de Mandragore et d’Initiale avait été mis en ligne par la société Logilab en 2015-2016, avant la naissance du portail Biblissima en 2017. 

Ce travail est au cœur de l’accès « [Iconographie](https://portail.biblissima.fr/fr/iconography) » du [portail Biblissima](https://portail.biblissima.fr/).

La plupart des alignements avec les fichiers d'autorité de la BnF inclus dans le présent export sont issus de ces travaux.
