
|:--------------------|:--------------------|:--------------------|
|[Home](./index.html)|[Ontology](./ontology.html)|[Example Knowledge Graph](./exampleKG.html)|

<h2 id="overview">Overview</h2>
> <p align="justify">This page demonstrates how and where our Metamine Ontology (MO) could be used. First we look at some SPARQL queries to query the <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example knowledge graph</a> and how those results will help. We then look at ways how 3-D large data files could be directly incorporated using the current framework by modifying the spreadsheet storing the data for knowledge graph. We then move forward to show how the ontology could be used for other types of metamaterials and outside the metamaterial domain. We conclude by exhibiting our vision of how our ontolgoy and its method could help create a knowledge graph of all the ontologies and knowledge graphs in the material science domain. </p>

|[Query](#sparql)|[MO extension and use by KG code modification to incorporate different metamaterials](#otherMeta)|[Vision](#vision)|

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
<br>

<h3> Other Possible Scenarios </h3>
> <p align="justify"> Other such queries could be queried over the created knowledge graph to extract the creator of the above metamaterial, or get metamaterials within a required effective property ranges, within the required property ranges, to find different contituent materials that could provide the required effective properties, use of labels for querying, and so on. </p>
>
> <p align="justify"> As different types 2D Structural Metamaterial is added to the knowledge graph, it will help the community to have access to the existing metamaterials and their provenance on their finger tips. this would also help the material scientists to save the energy and time that would have been used up only to know that the work they did was a duplicating of an existing work.</p>


<h2 id="otherMeta"><u>MO extension and use by KG code modification to incorporate different metamaterials</u></h2>

<h3> Orthotropic Metamaterials </h3>

> <p align="justify"> The data could be directly stored in a spreadsheet as shown in the below figure <p>

<iframe src="images/3D_data.png" style="width: 500px;height: 200px;border: none;"></iframe>


> <p align="justify"> The "Shear Modulus" needs to be added to the ontology under Properties and "Effective Shear Modulus" under Effective properties. The relations of these would be the same as those of "Youngs Modulus and Effective Youngs Modulus".</p>
> <p align="justify"> For creating the knowledge graph, we would add the above spreadsheet link in the geometry data column of the provided <a href="https://tetherless-world.github.io/metamine/exampleKG.html#exampleKG">sampleData template and add another column of effective shear mudulus</a>. The same <a href="https://github.com/tetherless-world/metamine/blob/master/setl/metamine_kg.ttl">knowledge graph setlr script</a> with a modification to incorporate 2 poissons ratio, two youngs modulus and one shear modulus could be run on this data set.</p>

<iframe src="images/3D_data_rep.png" style="width: 500px;height: 200px;border: none;"></iframe>

> <p align="justify">The resulted orthotropic metamaterial knowledge graph could be found <a href="https://raw.githubusercontent.com/tetherless-world/metamine/master/setl/orthotropic_metamaterial_kg.ttl">here</a>. The image below provides a snippet of the generated orthotropic metamaterial knowledge graph of the above example data. </p>

<iframe src="images/orthotropic_kg_snapshot.png" style="width: 500px;height: 200px;border: none;"></iframe>

><b>The same process could be followed for other 3D structural metamaterial dataset.</b>

<h3> Other types of Metamaterials </h3>

<p align="justify"> To apply the created MO to other types of metamaterials, we would be required to do one of the following two things:
<ol>
<li>Keep the ontology intact and made changes to the data storage method so that it looks exactly as the provided template</li>
<li>Extend MO by adding more properties and effective properties as required and then extend the KG code accordingly</li>
</ol>
This could be demonstrated by looking at <b>Acoustic Metamaterials</b>, <b>Knitting</b>, and <b>Origami</b></p>

<h4> Acoustic Metamaterial</h4>
> <p align="justify">As all other metamaterials, acoustic metamaterial also consists of constituent materials, its shape is described by a geometry and possesses some effective properties which are in relation to the constituent material properties. In addition, acoustic metamaterials has a thin film weight at the center, adding radius and film weight to the structure. The effective properties attained by these metamaterials are generally resonant bandgaps. The data could be stored in a spreadsheet as shown in the image below with addition of bandgaps columns.</p>

<iframe src="images/acoustic_data.png" style="width: 500px;height: 150px;border: none;"></iframe>


> <p align="justify">Our current ontology does consist of bandgap class, so an extension of the bandgap class could be done to add resonant bandgaps to it. Moreover, as film is created using a constituent material, hence that becomes a part of the constituent material with its attributes.However, the radius should be added as an extension to the geometry class of MO.</p>

<h4>Knitting</h4>
> <p align="justify"> According to the authors of <a href="https://journals.aps.org/prx/pdf/10.1103/PhysRevX.8.021075"> "Geometry and Elasticity of a knitted fabric" </a>, "knitting is not only a mere art and craft hobby but also a thousand-year-old technology", enabling "the engineering of arbitrarily shaped two- and three dimensional objects with tunable mechanical response". Their study claims to provide a fundamental framework that pave the way to thread-based smart materials by understanding knitted fabrics and its properties. A nylon thread is used to manufacture a 51x51 stockinette patterened stitched fabric using a machanical knitting machine (Toyota KS858 singlebed knitting machine). Length of upper and lower rows are fixed to 227mm. Statistics for inhomogeneous deformation were nylon-based monofilament (Stroft® GTM) of diameter d=80 μm and length of approximately 25 m, young's modulus= 5.1 GPa, yeilded bending modulus B ≈ 10^−8 J.m. Fig 3 in teh paper states that the geometry is similar to orthogonal. Since the data is a 3-D one so we would store the actual data in a different file and add the file link to our datasheet representing the metamaterial. One can read teh <a href="https://journals.aps.org/prx/pdf/10.1103/PhysRevX.8.021075">paper</a> for more information on knitting as a metamaterial and the whole process. The manually extracted data from the paper could be organized in a spreadsheet as shown in the figure below</p>

<iframe src="images/knitting_data.png" style="width: 500px;height: 150px;border: none;"></iframe>


><p align="justify"> As we can see in the data above, the template is exactly the same as our provided <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example data</a>, with the addition of flexural modulus and teh constituent material attributes. They could be easily incorporated in the knowledge graph by extending the property and effective property classes of our MO in addition to the modifications in data storage for KG creation as discussed in our <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example KG page</a>. </p>
>
><p align="justify">P.S: the data curated from the paper for this example is solely for demonstration purpose only.</p>

<h4>Origami</h4>

><p align="justify"> Please find details of origami as a metamaterial at <a href="https://par.nsf.gov/servlets/purl/10058688">this</a> article in Nature Physics. Origami could be looked as a structural metamaterial. Let's look at teh "MiuRa Fold" which is the zig zag based origami. The difference between these structural metamaterials than to teh once shown in the example knowledge graph section is that, on pulling the material outward we can see the edges go outward to instead of going in inward direction. This causes the material to possess a negative poisson's ratio which is generally not possessed by materials in nature. A knowledge graph of such materials could directly be craeted using the process defined in the <a href="https://tetherless-world.github.io/metamine/exampleKG.html">example KG page</a>. If the material used is a paper then constituent material 1 becomes paper and constituent material becomes void or air, while the effective poissons ratio would now consist of a negative value instead of a positive one.</p>

<h2 id="vision"><u>Vision</u></h2>

> <ol>
> <li align="justify">With metamaterials being comparatively a new research domain, hence one can find n-definitions of a metamaterial. It is difficult even for a material scientist to define a metamaterial in a concrete manner and in general many define it as "a material engineered to have a property that is not found in naturally occurring materials". This generalized definitions sometimes put researchers in a confused state. For example, <b>"phonomic crystals"</b> share a lot of attributes of that of <b>"photonic crystals"</b> which is a kind of optical metamaterial. But researchers are still debating whther they should be called as metamaterials or not.
> <ul>
> <li align="justify"> It is our vision to help metamaterial researchers understand the true definition of metamaterials with teh use of semantics. This could be easily done by getting all the available definitions available over the web in different pages and research work, and finding the hidden semantics meaning.</li>
> </li align="justify"> This will also help the researchers to difefrentiate between two types of materials, find the ways they are common and different from one another.</li>
> </ul>
> </li>
> <li align="justify">Our ontology the MO is different from other present material science ontolgoies as it is based fully on the material science interrelationship aspect presented by the <b>tetrahedron</b>. Hence, it focuses on the description of the material (metamaterial in this case), its representation (through geometry) and, its properties and the resultant properties (effective properties). this helps us incorporate most of teh unique challenges possessed by the metmaterial research. This also helps us to look at ways how all the material science ontologies and knowledge graphs could be combined together to have a connected platform for advanced research. To see if this is possible, we create <a href="https://raw.githubusercontent.com/tetherless-world/metamine/master/setl/materialsmine.ttl"MaterialsMine Ontology (MMO)</a> by combining Nanomine Ontology and Metamine Ontology. The conceptual model of MMO could be seen in the figure below.
> <ul>
> <li align="justify">This provides us with a vision of having a material sciece domain repository similar to BioPortal - a repository of biomedical ontolgoies.</li>
> </ul>
> </li>
> </ol>
<iframe src="images/materialsmine_ontology.pdf" style="width: 700px;height: 350px;border: none;"></iframe>



[back](./)
