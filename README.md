# Annotating Arguments in a Corpus of Opinion Articles

Corpus of opinion articles annotated with arguments presented at [LREC 2022](https://lrec2022.lrec-conf.org/en/). The annotation was conducted over a collection of 373 opinion articles from the Portuguese newspaper [Público](https://www.publico.pt/).   

## Citation 
```
@InProceedings{rocha-EtAl:2022:LREC,
  author    = {Rocha, Gil  and  Trigo, Luís  and  Lopes Cardoso, Henrique  and  Sousa-Silva, Rui  and  Carvalho, Paula  and  Martins, Bruno  and  Won, Miguel},
  title     = {Annotating Arguments in a Corpus of Opinion Articles},
  booktitle      = {Proceedings of the Language Resources and Evaluation Conference},
  month          = {June},
  year           = {2022},
  address        = {Marseille, France},
  publisher      = {European Language Resources Association},
  pages     = {1890--1899},
  url       = {https://aclanthology.org/2022.lrec-1.201}
}
```

> **Abstract:** Interest in argument mining has resulted in an increasing number of argument annotated corpora. However, most focus on English texts with explicit argumentative discourse markers, such as persuasive essays or legal documents. Conversely, we report on the first extensive and consolidated Portuguese argument annotation project focused on opinion articles. 
We briefly describe the annotation guidelines based on a multi-layered process and analyze the manual annotations produced, highlighting the main challenges of this textual genre. We then conduct a comprehensive inter-annotator agreement analysis, including argumentative discourse units, their classes and relations, and resulting graphs.
This analysis reveals that each of these aspects tackles very different kinds of challenges. 
We observe differences in annotator profiles, motivating our aim of producing a non-aggregated corpus containing the insights of every annotator.
We note that the interpretation and identification of token-level arguments is challenging; nevertheless, tasks that focus on higher-level components of the argument structure can obtain considerable agreement. 
We lay down perspectives on corpus usage, exploiting its multi-faceted nature. 

## JSON corpus structure
The JSON file contains the list of 373 articles in UTF-8 format. 
We include the page links for the original opinion articles and character-level indexes for the annotations. The article's raw text is not included due to copyright restrictions. 

Each article follows the structure:
```
    "_id": article unique identifier (MongoDB compliant)
    "authors": list of authors
    "url_canonical": original article url (Público online news editorial webpage)
    "publish_date": date of publication in the online news editorial
    "topics": article topics, from the set of topics considered in this project, namely: "desporto" ("sports"), "cultura" ("culture"), "local" ("local"), "economia" ("economy"), "mundo" ("world"), "sociedade" ("society"), "política" ("politics"), "ciência e tecnologia" ("sci-tech"). 
    "argument_annotations": list of annotations performed for this article. Each annotation follows the Argument Interchange Format (AIF) format (with some additional fields specific to the annotation platform used in this project, the ArgMine platform), with the following structure:
            "nodes": nodes list. Each node contains several fields (some of which are only relevant for the ArgMine Platform). The following fields are the most relevant:
                "id": node unique identifier
                "type": if "type" == "I", means that this node corresponds to an "Information" node, this is a node containing annotated text. Otherwise, it means that this node is a relation node. In this project we only consider two types of relations: Support relation ("type" == "RA") or Attack relation ("type" == "CA").
                "label": node classification type. If "type" == "I", in this project we consider the following node labels: "Facto", "Valor", "Valor(-)", "Valor(+)", "Diretiva". Otherwise, this field will have the value "nullADU".
                "ranges": char level indices of the annotated text. List of two integers values, where the first element corresponds to the first char in the annotated text and the last element to the last annotated char. Important to note that the indices range is open in the last char: \[start, end\[.
            "edges": directed edges list
                "from": id of the source node
                "to": id of the target node 
            "metadata":
                "annotatorId": annotator unique identifier
```

## Contact Persons
* Gil Rocha, gil.rocha@fe.up.pt
* Luís Trigo, ltrigo@fe.up.pt
* Henrique Lopes Cardoso, hlc@fe.up.pt
