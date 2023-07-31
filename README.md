# Organs Ontology
An ontology to describe organs, their properties and their evolution.

[![DOI](https://zenodo.org/badge/372536364.svg)](https://zenodo.org/badge/latestdoi/372536364)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

> 🔗 Ontology URI: [https://w3id.org/polifonia/ontology/organs/](https://w3id.org/polifonia/ontology/organs/)

The Organs ontology module of the [Polifonia ontology network](https://github.com/polifonia-project/ontology-network) represents concepts and relationships that describe pipe organs. The ontology describes the organ in a two-fold way:
- as a musical instrument that consists of parts 
- as a focal point of a project that describes the historical changes of the organ throughout the years.

![overview](diagrams/organs.jpg)

## Relevant statistics

- Number of classes:  33
- Number of object properties: 22
- Number of datatype properties: 12
- Number of logical axioms: 73

## Competency questions addressed by this ontology module

| **ID**   | **Competency question**                                              |
| -------- | -------------------------------------------------------------------- |
| **CQ1**  | Who built and/or renovated an organ?                                 |
| **CQ2**  | What was the disposition of the organ at a specific point in time?   |
| **CQ3**  | What are the original parts of the organ?                            |
| **CQ4**  | Where are the original parts of an organ?                            |
| **CQ5**  | Where is an organ located originally?                                |
| **CQ6**  | When is an organ moved to another location?                          |
| **CQ7**  | Why is an organ moved to another location?                           |

## Competency questions that will be addressed by this ontology module

| **ID**   | **Competency question**                                              |
| -------- | -------------------------------------------------------------------- |
| **CQ8**  | What are the sources of the project that an organ is involved in?    |
| **CQ9**  | Which resources mention an organ?                                    |
| **CQ10** | Which resources mention an organ builder?                            |


## Examples of SPARQL queries addressed by the module

- Who built an organ? 
```
PREFIX organs: <https://w3id.org/arco/ontology/organs/>
PREFIX core: <https://w3id.org/arco/ontology/core/>

SELECT DISTINCT ?agent
WHERE { 
?organ core:isDescribedBy ?project .
?project core:hasAgentRole ?agentRole .
?agentRole core:hasRole ?role .

FILTER(str(?role)='builder')
}
```

- What was the disposition of the organ at a specific point in time?
```
PREFIX organs: <https://w3id.org/arco/ontology/organs/>
PREFIX core: <https://w3id.org/arco/ontology/core/>

SELECT DISTINCT ?partHood ?timeinterval
WHERE { 
?organ core:isWholeincludedIn ?parthood . 
?parthood a core:Parthood .
?parthood core:hasTimeInterval ?timeInterval .

```

- Where is an organ located originally?  
```
PREFIX organs: <https://w3id.org/arco/ontology/organs/>
PREFIX core: <https://w3id.org/arco/ontology/core/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT DISTINCT ?place
WHERE { 
?organ core:isDescribedBy ?project .
?project core:hasPlace ?place .
?place a core:PhysicalPlace . 
?project core:isFirstProject ?isFirstProject .
FILTER(xsd:Boolean(?isFirstProject) = True)
```


## Imported ontologies

### Imported from the Polifonia Ontology Network

- [Core Module](https://github.com/polifonia-project/core-ontology/)

## Licence 
CC BY

