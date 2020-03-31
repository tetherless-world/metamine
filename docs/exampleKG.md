
|:--------------------|:--------------------|:--------------------|
|[Home](./index.html)|[Ontology](./ontology.html)|[Applications](./applications.html)|

<h2 id="overview">Overview</h2>
> <p align="justify">This page consists of a step by step process of how to create a knowldge graph using our ontology for structural metamaterials. It also provides an example knowledge graph. The same process with some modifications could be used to create knowledge graphs for other types of metamaterials also. </p>

|[Workflow](#workflow)|[Example Knowledge Graph](#exampleKG)|

<h2 id="workflow">Workflow</h2>
> <p align="justify">The diagram below depicts the workflow used to create a knowledge graph from a geometry.</p>

<iframe src="images/workflow_kg.pdf" style="width: 800px;height: 350px;border: none;"></iframe>

> <p align="justify">Data could be directly entered into the system by the authors or could be curated from published works and added to the system by researchers.</p>
> <p align="justify">Data should be entered on an online spreadsheet such as google sheets for easy accessibility.</p>
> <p align="justify">The customized SETLr script on Whyis converts the data from the spreadsheet to a knowledge graph. The structure of which is provided by our Metamine Ontology.</p>

<h2 id="exampleKG">Example Knowledge Graph</h2>
> <p align="justify">The example knowledge graph was created using the above method for 2-D isometric static metamaterials. The sample data used to create the example knowledge graph is shown in the figure below. </p>

<iframe src="images/MetamineSampleData.pdf" style="width: 800px;height: 350px;border: none;"></iframe>

> <p align="justify"> The above sample data was converted to a knowledge graph by using the customized setlr script, which could be found at <a href="https://github.com/tetherless-world/metamine/blob/master/setl/materialsmine_kg.setl.ttl"> https://github.com/tetherless-world/metamine/blob/master/setl/materialsmine_kg.setl.ttl <a> which incorporates our MO for providing structure to the generated knowledge graph.</p>

[back](./)