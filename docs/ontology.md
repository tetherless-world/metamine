
|:--------------------|:--------------------|:--------------------|
|[Home](./index.html)|[Example Knowledge Graph](./exampleKG.html)|[Applications](./applications.html)|

<h2 id="overview">Overview</h2>
> <p align="justify">This page consists of the concept map and the step-by-step process of ontology creation </p>

|[Conceptual Model](#conceptmap)|[Ontology File](#ontology)|[Ontologies Reused](#reused)|

<h2 id="conceptmap">Conceptual Model</h2>
<iframe src="images/metamine_ontology.pdf" style="width: 700px;height: 350px;border: none;"></iframe>
>An overview of the main classes and their property associations.

<h2 id="ontology">Ontology File</h2>
<b>Link:</b><a href="https://raw.githubusercontent.com/tetherless-world/metamine/master/setl/metamine.ttl"> https://raw.githubusercontent.com/tetherless-world/metamine/master/setl/metamine.ttl </a> <br>
<b>View the ontology documentation at:</b><a href="">add link here</a>

<h3>Primary Classes and Definitions</h3>
><ol>
><li>Constituent Material
><ul type="circle">
><li>Definition: A material entity is a physical entity that is spatially extended, exists as a whole at any point in time and has mass</li>
><li>Immediate Superclass: None</li>
><li>Reused: http://semanticscience.org/resource/SIO_000004 </li>
></ul>
></li>
>
><li>MetaMaterial
><ul type="circle">
><li>Definition: A material engineered to have a property that is not found in naturally occurring materials</li>
><li>Immediate Superclass: Constituent Material</li>
><li>Reused: None</li>
></ul>
></li>
>
><li>Geometry
><ul type="circle">
><li>Definition: An information content entity that pertains to the structure and topology of a metamaterial.</li>
><li>Immediate Superclass: http://semanticscience.org/resource/SIO_000506</li>
><li>Reused: None</li>
></ul>
></li>
>
><li>Property
><ul type="circle">
><li>Definition: An attribute of the constituent material.</li>
><li>Immediate Superclass: http://semanticscience.org/resource/SIO_000052</li>
><li>Reused: None</li>
></ul>
></li>
>
><li>Effective Property
><ul type="circle">
><li>Definition: An attribute of the metamaterial.</li>
><li>Immediate Superclass: http://semanticscience.org/resource/SIO_000052</li>
><li>Reused: None</li>
></ul>
></li>
>
></ol>

<h2 id="reused">Ontologies Reused</h2>




[back](./)