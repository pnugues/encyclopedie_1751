# Raccordement des articles géographiques de l'_Encyclopédie_ de Diderot à Wikidata

_For a summary in English, see below._

L’_Encyclopédie_ de Diderot est le plus grand ouvrage de référence du XVIIIe siècle. Il vise à rassembler tous les savoirs de son époque. Ce dépôt héberge un ensemble de données annotées de plus de 9 700 articles de l'_Encyclopédie_ avec des identifiants Wikidata. Ils nous permettent de connecter ces articles au graphe Wikidata.

## Jeu de données
Nous avons extrait la totalité des 15 274 articles géographiques et nous avons complètement annoté tous les articles contenant une description d'êtres humains. Cela représente plus de 2 600 liens renvoyant à des lieux ou à des êtres humains. De plus, nous avons annoté plus de 8 800 articles ayant un contenu uniquement géographique.

Nous avons stocké l'ensemble de données dans le fichier JSON `encyclo_diderot_wd.json`. Il se compose d'une liste de dictionnaires Python, où chaque dictionnaire représente un article géographique de l'_Encyclopédie_. Un dictionnaire Python contient :
    - La vedette de l'article (clé `vedette`),
    - le texte de l'article (touche `texte`),
    - l'identifiant d'article dans la version OCR de l'ENCCRE (http://enccre.academie-sciences.fr/encyclopedie/) (clé `entreeid`), et
    - une liste d'identifiants wikidata, si l'article est annoté (clé `qid`).

Par exemple, l'entrée _Grenoble_ décrit la ville de Grenoble et contient la biographie de deux juristes, Guy Pape et Jean Pierre Moret. Nous avons alors une liste de trois QID :<br/>```{'vedette': 'GRENOBLE', 'entreeid': 'v7-1475-0', 'texte': 'GRENOBLE, Gratianopolis, (Géogr.)\u200b ancienne ville de France, capitale du Dauphiné, avec un évêché suffragant de Vienne, & un parlement érigé en 1493 par Louis XI. qui n’étoit encore que dauphin ; ... On met au nombre des jurisconsultes dont Grenoble est la patrie, Pape (Guy), qui mourut en 1487 ; son recueil de décisions des plus belles questions de droit, n’est pas encore tombé dans l’oubli.\n\n\nM. de Bouchenu de Valbonnais, (Jean Pierre Moret) premier président du parlement de Grenoble, né dans cette ville le 23 Juin 1651, mérite le titre du plus savant historiographe de son pays, ... (D. J.)\u200b', 'qid': ['Q1289', 'Q41617345', 'Q3169582']}```

De plus, un dictionnaire peut contenir :
* Une clé `note` qui donne une indicaction sur la façon dont nous avons trouvé l'identifiant
* Une clé `renvoi` où la valeur du `renvoi` contient l'`entreeid` cible dans la nomenclature ENCCRE. Dans ce cas, il n’y a pas de `qid`.
* Une clé `qid_region` s'il n'y a pas de QID. Nous avons divisé le monde en 32 régions et nous avons attribué une région à chaque article que nous n'avons pas eu le temps d'annoter.

## Summary in English
Diderot’s _Encyclopédie_ is a reference work from XVIIIth century in Europe that aimed at collecting the knowledge of its era. This repository hosts an annotated dataset of more than 9,700 of the _Encyclopédie_ entries with Wikidata identifiers enabling us to connect these entries to the Wikidata graph. 

We extracted all the 15,274 geographic entries and we completely annotated all the entries containing a description of human entities. This represents more than 2,600 links referring to locations or human entities. In addition, we annotated more than 8,800 entries having a geographic content only. 

We stored the dataset in the `encyclo_diderot_wd.json` JSON file. It consists of a list of Python dictionaries, where each dictionary represents a geographic entry from the _Encyclopédie_. A Python dictionary contains:
   -  The entry headword (`vedette` key),
   -  the text of the entry (`texte` key),
   -  the entry identifier in the OCR version from ENCCRE (http://enccre.academie-sciences.fr/encyclopedie/) (`entreeid` key), and
   -  a list of wikidata identifiers, if it is annotated (`qid` key).

For example, the _Grenoble_ entry describes the city of Grenoble and contains the biography of two lawyers, Guy Pape and Jean Pierre Moret. We have then a list of three QIDs:<br/>```{'vedette': 'GRENOBLE', 'entreeid': 'v7-1475-0', 'texte': 'GRENOBLE, Gratianopolis, (Géogr.)\u200b ancienne ville de France, capitale du Dauphiné, avec un évêché suffragant de Vienne, & un parlement érigé en 1493 par Louis XI. qui n’étoit encore que dauphin ; ... On met au nombre des jurisconsultes dont Grenoble est la patrie, Pape (Guy), qui mourut en 1487 ; son recueil de décisions des plus belles questions de droit, n’est pas encore tombé dans l’oubli.\n\n\nM. de Bouchenu de Valbonnais, (Jean Pierre Moret) premier président du parlement de Grenoble, né dans cette ville le 23 Juin 1651, mérite le titre du plus savant historiographe de son pays, ... (D. J.)\u200b', 'qid': ['Q1289', 'Q41617345', 'Q3169582']}```

In addition, a dictionary may contain:
* A `note` key that gives a hint on how we found the identifier
* A `renvoi` key if this entry is a cross-reference. The `renvoi` value contains the target `entreeid`. In this case, there is no `qid`. 
* A `qid_region` key if there is no QID. We have partitioned the world into 32 regions and we assigned one region to each entry that we did not have the time to annotate.
   
* A `src` folder that contains:
    * `raccordement_larousse.ipynb`, a Jupyter notebook which shows how to read and use of the json file;
    * `larousse_1905_wd_extraction.json`, a file which adds information extracted from wikidata to articles;
* A `docs` folder that contains:
   * The poster presented at LREC 2022, see the reference below;
   * Slides describing the dataset and how I created it.

If you use this dataset, please cite the references below.
## Citer ce jeu de données
Si vous utilisez ce jeu de données, merci d'en citer l'origine avec les références suivantes :

```
@InProceedings{nugues:2022:LREC,
  author    = {Nugues, Pierre},
  title     = {Connecting a French Dictionary from the Beginning of the 20th Century to Wikidata},
  booktitle      = {Proceedings of the Language Resources and Evaluation Conference},
  month          = {June},
  year           = {2022},
  address        = {Marseille, France},
  publisher      = {European Language Resources Association},
  pages     = {2548--2555},
  abstract  = {The Petit Larousse illustré is a French dictionary first published in 1905. Its division in two main parts on language and on history and geography corresponds to a major milestone in French lexicography as well as a repository of general knowledge from this period. Although the value of many entries from 1905 remains intact, some descriptions now have a dimension that is more historical than contemporary. They are nonetheless significant to analyze and understand cultural representations from this time. A comparison with more recent information or a verification of these entries would require a tedious manual work. In this paper, we describe a new lexical resource, where we connected all the dictionary entries of the history and geography part to current data sources. For this, we linked each of these entries to a wikidata identifier. Using the wikidata links, we can automate more easily the identification, comparison, and verification of historically-situated representations. We give a few examples on how to process wikidata identifiers and we carried out a small analysis of the entities described in the dictionary to outline possible applications. The resource, i.e. the annotation of 20,245 dictionary entries with wikidata links, is available from GitHub (https://github.com/pnugues/petit\_larousse\_1905/)},
  url       = {https://aclanthology.org/2022.lrec-1.272}
}

@misc{pnugues2021,
  author = {Pierre Nugues},
  title = {Raccordement du {Petit Larousse illustré} de 1905 à wikidata},
  year = 2021,
  url = {https://github.com/pnugues/petit_larousse_1905}
}
```
## Remerciements
J'ai réalisé moi-même et manuellement tous les raccordements entre les noms propres et les identifiants wikidata.

Le texte provient de la dernière version ENCCRE
