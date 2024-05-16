# Raccordement des articles géographiques de l'_Encyclopédie_ de Diderot à Wikidata

_For a summary in English, see below._

L’_Encyclopédie_ de Diderot est le plus grand ouvrage de référence du XVIIIe siècle. Il vise à rassembler les savoirs de son époque. L’_Encyclopédie_ classe les articles par grands domaines comme la géographie, la botanique, l'économie, etc.

Ce dépôt héberge un jeu de données contenant 15 274 articles de géographie dont 9 700 sont annotés avec des identifiants Wikidata. Ces identifiants nous permettent de connecter les articles au graphe Wikidata et à Wikipedia.

## Jeu de données
Nous avons extrait la totalité des 15 274 articles géographiques l’_Encyclopédie_. Certains de ces articles contiennent des biographies. Nous avons complètement annoté tous les articles correspondants. Cela représente plus de 2 600 liens renvoyant à des lieux ou à des êtres humains. Nous avons aussi annoté plus de 8 800 articles ayant uniquement une description géographique.

Nous avons stocké le jeu de données dans le fichier JSON `diderot_1751_wd.json`. Il se compose d'une liste de dictionnaires Python, où chaque dictionnaire correspond à un article géographique de l'_Encyclopédie_. Un dictionnaire Python contient :
- La vedette de l'article (clé `vedette`),
- le texte de l'article (clé `texte`),
- l'identifiant d'article dans la version OCR de l'ENCCRE (http://enccre.academie-sciences.fr/encyclopedie/) (clé `entreeid`), et
- une liste d'identifiants wikidata lorsque l'article est annoté (clé `qid`).

Par exemple, l'article _Grenoble_ décrit la ville de Grenoble et contient la biographie de deux juristes, Guy Pape et Jean Pierre Moret. La clé `qid` du dictionnaire Python est une liste de trois QIDs pour Grenoble et ces deux auteurs. Le dictionnaire complet est le suivant :<br/>```{'vedette': 'GRENOBLE', 'entreeid': 'v7-1475-0', 'texte': 'GRENOBLE, Gratianopolis, (Géogr.)\u200b ancienne ville de France, capitale du Dauphiné, avec un évêché suffragant de Vienne, & un parlement érigé en 1493 par Louis XI. qui n’étoit encore que dauphin ; ... On met au nombre des jurisconsultes dont Grenoble est la patrie, Pape (Guy), qui mourut en 1487 ; son recueil de décisions des plus belles questions de droit, n’est pas encore tombé dans l’oubli.\n\n\nM. de Bouchenu de Valbonnais, (Jean Pierre Moret) premier président du parlement de Grenoble, né dans cette ville le 23 Juin 1651, mérite le titre du plus savant historiographe de son pays, ... (D. J.)\u200b', 'qid': ['Q1289', 'Q41617345', 'Q3169582']}```

De plus, un dictionnaire peut contenir :
* Une clé `note` qui donne une indicaction sur la façon dont nous avons trouvé l'identifiant ;
* Une clé `renvoi`. Certains articles de _Encyclopédie_ ne sont qu'un renvoi à un autre article. Dans ce cas, la valeur de la clé `renvoi` est l'`entreeid` cible dans la nomenclature ENCCRE. Un article avec un `renvoi` n’a pas de `qid`;
* Une clé `qid_region` s'il n'y a pas de QID. Nous avons divisé le monde en 32 régions et nous avons attribué une région à chaque article que nous n'avons pas eu le temps d'annoter.

## Citer ce jeu de données
Si vous utilisez ce jeu de données, merci d'en citer l'origine avec les références suivantes :

```
@InProceedings{nugues:2024:LREC,
  author    = {Nugues, Pierre},
  title     = {Linking Named Entities in Diderot's Encyclopédie to Wikidata},
  booktitle      = {Proceedings of the Language Resources and Evaluation Conference},
  month          = {May},
  year           = {2024},
  address        = {Torino, Italy},
  publisher      = {European Language Resources Association},
}

@misc{pnugues2024,
  author = {Pierre Nugues},
  title = {Raccordement de l'{Encyclopédie} de Diderot à Wikidata},
  year = 2024,
  url = {https://github.com/pnugues/encyclopedie_1751}
}
```
## Remerciements
Le texte provient du site ENCCRE (http://enccre.academie-sciences.fr/encyclopedie/), lui-même provenant de Wikisource (https://fr.wikisource.org/wiki/Encyclopédie,_ou_Dictionnaire_raisonné_des_sciences,_des_arts_et_des_métiers).

J'ai réalisé moi-même et manuellement tous les raccordements entre les articles et les identifiants wikidata.

## Summary in English
Diderot’s _Encyclopédie_ is a reference work from XVIIIth century in Europe that aimed at collecting the knowledge of its era. This repository hosts an annotated dataset of more than 9,700 of the _Encyclopédie_ entries with Wikidata identifiers enabling us to connect these entries to the Wikidata graph. 

We extracted all the 15,274 geographic entries and we completely annotated all the entries containing a description of human entities. This represents more than 2,600 links referring to locations or human entities. In addition, we annotated more than 8,800 entries having a geographic content only. 

We stored the dataset in the `diderot_1751_wd.json` JSON file. It consists of a list of Python dictionaries, where each dictionary represents a geographic entry from the _Encyclopédie_. A Python dictionary contains:
   -  The entry headword (`vedette` key),
   -  the text of the entry (`texte` key),
   -  the entry identifier in the OCR version from ENCCRE (http://enccre.academie-sciences.fr/encyclopedie/) (`entreeid` key), and
   -  a list of wikidata identifiers, if it is annotated (`qid` key).

For example, the _Grenoble_ entry describes the city of Grenoble and contains the biography of two lawyers, Guy Pape and Jean Pierre Moret. We have then a list of three QIDs:<br/>```{'vedette': 'GRENOBLE', 'entreeid': 'v7-1475-0', 'texte': 'GRENOBLE, Gratianopolis, (Géogr.)\u200b ancienne ville de France, capitale du Dauphiné, avec un évêché suffragant de Vienne, & un parlement érigé en 1493 par Louis XI. qui n’étoit encore que dauphin ; ... On met au nombre des jurisconsultes dont Grenoble est la patrie, Pape (Guy), qui mourut en 1487 ; son recueil de décisions des plus belles questions de droit, n’est pas encore tombé dans l’oubli.\n\n\nM. de Bouchenu de Valbonnais, (Jean Pierre Moret) premier président du parlement de Grenoble, né dans cette ville le 23 Juin 1651, mérite le titre du plus savant historiographe de son pays, ... (D. J.)\u200b', 'qid': ['Q1289', 'Q41617345', 'Q3169582']}```

In addition, a dictionary may contain:
* A `note` key that gives a hint on how we found the identifier
* A `renvoi` key if this entry is a cross-reference. The `renvoi` value contains the target `entreeid`. In this case, there is no `qid`. 
* A `qid_region` key if there is no QID. We have partitioned the world into 32 regions and we assigned one region to each entry that we did not have the time to annotate.

If you use this dataset, please cite the references above.
