# Annotating Arguments in a Corpus of Opinion Articles
===============

Argument Corpus presented at [LREC 2022](https://lrec2022.lrec-conf.org/en/). The annotation was conducted over a corpus of 373 opinion articles collected from the Portuguese newspaper [Público](https://www.publico.pt/). The JSON file contains page links to the articles and character indexes on the text body of the annotations. The articles raw text is not included.  Do you want to use this corpus and need help or have a pressing request/doubt? Please, contact us.

> **Abstract:** Interest in argument mining has resulted in an increasing number of argument annotated corpora. However, most focus on English texts with explicit argumentative discourse markers, such as persuasive essays or legal documents. Conversely, we report on the first extensive and consolidated Portuguese argument annotation project focused on opinion articles. 
We briefly describe the annotation guidelines based on a multi-layered process and analyze the manual annotations produced, highlighting the main challenges of this textual genre. We then conduct a comprehensive inter-annotator agreement analysis, including argumentative discourse units, their classes and relations, and resulting graphs.
This analysis reveals that each of these aspects tackles very different kinds of challenges. 
We observe differences in annotator profiles, motivating our aim of producing a non-aggregated corpus containing the insights of every annotator.
We note that the interpretation and identification of token-level arguments is challenging; nevertheless, tasks that focus on higher-level components of the argument structure can obtain considerable agreement. 
We lay down perspectives on corpus usage, exploiting its multi-faceted nature. 

**Authors:** Gil Rocha, Luís Trigo, Henrique Lopes Cardoso, Rui Sousa-Silva, Paula Carvalho, Bruno Martins, Miguel Won

## Contact Persons
* Gil Rocha, gil.rocha@fe.up.pt
* Luís Trigo, ltrigo@fe.up.pt
* Henrique Lopes Cardoso, hlc@fe.up.pt

## JSON corpus structure
The JSON file contains the list of 373 articles in UTF-8 format. Each article follows the structure:

    "_id": article unique identifier (MongoDB compliant)
    "authors": list of authors
    "url_canonical": original article url (Público online news editorial webpage)
    "publish_date": article date of publication in the online news editorial
    "meta_description": article summary (short paragraph), typically included in the beginning of the article
    "topics": article topics, from the set of topics considered in this project (namely, "desporto", "cultura", "local", "economia", "mundo", "sociedade", "política", "ciência e tecnologia"). 
    "argument_annotations": list of annotations performed for this article. Each annotation follows the Argument Interchange Format (AIF) format (with some extra fields), with the following structure:
            "nodes": nodes list. Each node contains several fields (most of which are only relevant for the ArgMine Platform). The following fields are the most relevant:
                "id": node unique identifier
                "text": annotated text
                "type": if "type" == "I", means that this node correspond to an "Information" node, this is a node containing annotated text. Else, means that this node is a relation node. In this project we only consider two types of relations: Support relation ("type" == "RA") or Attack relation ("type" == "CA").
                "label": node classification type. If "type" == "I", in this project we consider the following node types: "Facto", "Valor", "Valor(-)", "Valor(+)", "Diretiva". Else, this field will have the value "nullADU".
                "ranges": char level indices of the annotated text from the article "body". List of two integers values, where the first element correspond to the first char in the annotated text and the last element to the last annotated char. Important to note that the indices range is open in the last char: \[start, end\[.
            "edges": directed edges list
                "from": id of the source node
                "to": id of the target node 
            "metadata": this metadata is used in the ArgMine Platform, the only relevant field for these purposes is:
                "annotatorId": annotator unique identifier
