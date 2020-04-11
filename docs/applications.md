
|:--------------------|:--------------------|:--------------------|
|[Home](./index.html)|[Ontology](./ontology.html)|[Example Knowledge Graph](./exampleKG.html)|

<h2 id="overview">Overview</h2>
> <p align="justify">This page demonstrates how and where our Metamine Ontology (MO) could be used. First we look at some SPARQL queries to query the <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example knowledge graph</a> and how those results will help. We then look at ways how 3-D large data files could be directly incorporated using the current framework by modifying the spreadsheet storing the data for knowledge graph. We then move forward to show how the ontology could be used for other types of metamaterials and outside the metamaterial domain. We conclude by exhibiting our vision of how our ontolgoy and its method could help create a knowledge graph of all the ontologies and knowledge graphs in the material science domain. </p>

|[Query](#sparql)|[3-Dimensional Structural Metamaterials](#3d)|[Other Types of Metamaterials](#otherMeta)|[Vision](#vision)|

<h2 id="sparql">Query</h2>

<h3>Scenario 1: Existing Metamaterial </h3>
> <strong> Query 1: Does a 2D structural Metamaterial with Effective Poissons Ratio "0.288084" and EffectiveYoungsModulus "1.55E+09 Pa" exists ? </strong>

    PREFIX sio: <http://semanticscience.org/resource/>
    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX metamine: <http://metamine.org/>

    SELECT DISTINCT ?material_id WHERE
    {
        ?material_id a metamine:Metamaterial ;
           sio:hasAttribute ?pr ;
           sio:hasAttribute ?ym .
        ?pr a metamine:EffectivePoissonsRatio ;
            sio:hasValue "0.288084"^^<xsd:double> ;
            sio:inRelationTo ?prmat .
        ?ym a metamine:EffectiveYoungsModulus ;
            sio:hasValue "1.55E+09"^^<xsd:double> ;
            sio:inRelationTo ?ymmat .
    } 
    

> <strong> Result 1: Existing 2D Structural Metamaterial retrieved from the match query is represented </strong>

<iframe src="images/query1output.png" style="width: 300px;height: 150px;border: none;"></iframe>

> <strong> Query 2: Provide constituent materials used and the basic geometry details of the above structural metamaterial ? </strong>

    PREFIX sio: <http://semanticscience.org/resource/>
    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX metamine: <http://metamine.org/>

    SELECT DISTINCT ?metamaterial_id ?constituent_materials_used ?geometry ?geometry_description WHERE
    {
    ?metamaterial_id a metamine:Metamaterial ;
        sio:hasAttribute ?pr ;
        sio:hasAttribute ?ym ;
        sio:hasPart ?constituent_materials_used ;
        sio:isDescribedBy ?geometrytype .
    ?pr a metamine:EffectivePoissonsRatio ;
                sio:hasValue "0.288084"^^<xsd:double> ;
                sio:inRelationTo ?prmat .
            ?ym a metamine:EffectiveYoungsModulus ;
                sio:hasValue "1.55E+09"^^<xsd:double> ;
                sio:inRelationTo ?ymmat .
    ?geometrytype sio:hasValue ?geometry ;
                rdfs:label ?geometry_description .
    } 

> <strong> Result 1: Information on the constituent materials used and basic geometry details of the existing 2D Structural Metamaterial retrieved from the match query is represented </strong>

<iframe src="images/query2output.png" style="width: 300px;height: 150px;border: none;"></iframe>

<h3> Other Possible Scenarios </h3>
> <p align="justify"> Other such queries could be queried over the created knowledge graph to extract the creator of the above metamaterial, or get metamaterials within a required effective property ranges, within the required property ranges, to find different contituent materials that could provide the required effective properties, and so on. </p>
>
> <p align="justify"> As du=ifferent types 2D Structural Metamaterial is added to the knowledge graph, it will help the community to have access to the existing metamaterials and their provenance on their finger tips. this would also help the material scientists to save the energy and time that would have been used up only to know that the work they did was a duplicating of an existing work.  

<h2 id="3d">3-Dimensional Structural Metamaterials</h2>


[back](./)