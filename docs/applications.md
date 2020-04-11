
|:--------------------|:--------------------|:--------------------|
|[Home](./index.html)|[Ontology](./ontology.html)|[Example Knowledge Graph](./exampleKG.html)|

<h2 id="overview">Overview</h2>
> <p align="justify">This page demonstrates how and where our Metamine Ontology (MO) could be used. First we look at some SPARQL queries to query the <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example knowledge graph</a> and how those results will help. We then look at ways how 3-D large data files could be directly incorporated using the current framework by modifying the spreadsheet storing the data for knowledge graph. We then move forward to show how the ontology could be used for other types of metamaterials and outside the metamaterial domain. We conclude by exhibiting our vision of how our ontolgoy and its method could help create a knowledge graph of all the ontologies and knowledge graphs in the material science domain. </p>

|[Query](#sparql)|[Extension of Current Ontology](#extension)|[Other Types of Metamaterials](#otherMeta)|[Vision](#vision)|

<h2 id="sparql"><u>Query</u></h2>

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
<iframe src="images/query1output.png" style="width: 300px;height: 100px;border: none;"></iframe>
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

<iframe src="images/query2output.png" style="width: 500px;height: 150px;border: none;"></iframe>


<h3> Other Possible Scenarios </h3>
> <p align="justify"> Other such queries could be queried over the created knowledge graph to extract the creator of the above metamaterial, or get metamaterials within a required effective property ranges, within the required property ranges, to find different contituent materials that could provide the required effective properties, use of labels for querying, and so on. </p>
>
> <p align="justify"> As different types 2D Structural Metamaterial is added to the knowledge graph, it will help the community to have access to the existing metamaterials and their provenance on their finger tips. this would also help the material scientists to save the energy and time that would have been used up only to know that the work they did was a duplicating of an existing work.</p>


<h2 id="extension"><u>Extension of Current Ontology</u></h2>

<h3> Orthotropic Metamaterials </h3>

> <p align="justify"> The data could be directly stored in a spreadsheet as shown in the below figure <p>

<iframe src="images/3D_data.png" style="width: 500px;height: 200px;border: none;"></iframe>


> <p align="justify"> The "Shear Modulus" needs to be added to the ontology under Properties and "Effective Shear Modulus" under Effective properties. The relations of these would be the same as those of "Youngs Modulus and Effective Youngs Modulus".</p>
> <p align=justify"> For creating the knowledge graph, we would add the above spreadsheet link in the geometry data column of the provided <a href="https://tetherless-world.github.io/metamine/exampleKG.html#exampleKG">sampleData template and add another column of effective shear mudulus</a>. The same <a href="https://github.com/tetherless-world/metamine/blob/master/setl/metamine_kg.ttl">knowledge graph setlr script</a> with a modification to incorporate 2 poissons ratio, two youngs modulus and one shear modulus could be run on this data set.</p>

<iframe src="images/3D_data_rep.png" style="width: 500px;height: 200px;border: none;"></iframe>
> <p align="justify">The resulted orthotropic metamaterial knowledge graph could be found <a href="https://github.com/tetherless-world/metamine/blob/master/setl/orthotropic_metamaterial_kg.ttl>here</a>. </p>

><b>The same process could be followed for other 3D metamaterial dataset.</b>

[back](./)