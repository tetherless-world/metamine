
|:--------------------|:--------------------|:--------------------|
|[Home](./index.html)|[Ontology](./ontology.html)|[Example Knowledge Graph](./exampleKG.html)|

<h2 id="overview">Overview</h2>
> <p align="justify">This page demonstrates how and where our Metamine Ontology (MO) could be used. First we look at some SPARQL queries to query the <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example knowledge graph</a> and how those results will help. We then look at ways how 3-D large data files could be directly incorporated using the current framework by modifying the spreadsheet storing the data for knowledge graph. We then move forward to show how the ontology could be used for other types of metamaterials and outside the metamaterial domain. We conclude by exhibiting our vision of how our ontolgoy and its method could help create a knowledge graph of all the ontologies and knowledge graphs in the material science domain. </p>

|[Query](#sparql)|[3-Dimensional Structural Metamaterials](#3d)|[Other Types of Metamaterials](#otherMeta)|[Vision](#vision)|

<h2 id="sparql">Query</h2>

<h3>Scenario 1: Existing Metamaterial </h3>
> <strong> Query 1: Does a 2D structural Metamaterial with Effective Poissons Ratio "0.306472" and EffectiveYoungsModulus "1.80E+09 Pa" exists ? </strong>

    <pre>
        PREFIX sio: <http://semanticscience.org/resource/>
        PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
        PREFIX owl: <http://www.w3.org/2002/07/owl#>
        PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
        PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
        PREFIX metamine: <http://metamine.org/>

        SELECT DISTINCT ?s WHERE{
            ?s a metamine:Metamaterial ;
            sio:hasAttribute ?pr ;
            sio:hasAttribute ?ym .
            ?pr a metamine:EffectivePoissonsRatio ;
                sio:hasValue "0.306472"^^<xsd:double> ;
                sio:inRelationTo ?prmat .
            ?ym a metamine:EffectiveYoungsModulus ;
                sio:hasValue "1.80E+09"^^<xsd:double> ;
                sio:inRelationTo ?ymmat .
        } 
    </pre>

> <strong> Result 1: Existing 2D Structural Metamaterial retrieved from the match query is represented </strong>
> <iframe src="images/query1output.png" style="width: 300px;height: 150px;border: none;"></iframe>

<h2 id="3d">3-Dimensional Structural Metamaterials</h2>


[back](./)