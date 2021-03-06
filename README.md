# The GTFS-Madrid-Bench

We present the GTFS-Madrid-Bench, a benchmarking for virutal knowledge graph access in the transport domain. We use the de-facto standard model for publishing open data on web, GTFS, and we scale up and distribute the original dataset in several formats and sizes. This repository contains the following resources:

- Data: we have generated from several datasets(GTFS-[1,5,10,50,100,500]) in multiple formats (CSV, JSON, XML, SQL, MongoDB). The preparation script will download all these datasets and generate a docker-image for each dataset which is contained in a database (MySQL and MongoDB). All the datasets generated by this benchmark have to follow the license of the Consorcio Regional de Transporte de Madrid: https://www.crtm.es/licencia-de-uso?lang=en
- Generation: If any practicioner or developer wants to create datasets with other scale values all the resources are available.
- Queries: 18 queries increasing in terms of complexity.
- Mappings: 1 R2RML mapping document, 7 RML mapping document, 1 xR2RML mapping document, 1 YARRRML mapping and 1 CSVW annotations
- Engines: docker-compose with all the tested engines and running scripts


## Steps for using the Madrid-GTFS-Bench

1. If the datasets generated by us are enough for your testing:
	1. Go to the Data folder and read the instructions there to prepare the data in your local machine
2. If you want to generate other sizes from the input dataset:
	1. Go to the Generation folder and read the instructions to generate and distribute the data with the scale you need.
	2. If you need other type of format, add the corresponding transformation script (CSV2yourFormart) and run it after the generation process. 
	3. Go to point 1 (you have to modify data-preparation.sh in order to add your generated datasets)
3. Go to the mappings folder and select the files needed for your engine or modify one of them to adapt it to your format.
4. Go to the query folder and get the queries inside the VIG folder.
5. If you have a docker image of your engine go to the engines folder and add it to the docker-compose.yml. Note that you have to follow the same configuration as the other engines (i.e. shared volumes of data, results, mappings and queries) to be accesible your engine. You can remove the generation of the rest engines.
6. Prepare your run script and obtain the results. Examples of these scripts are provided inside each engine folder.

## Baseline:
In order to test the completeness of each engine we have also materialized the generated datasets using the [SDM-RDFizer](https://github.com/SDM-TIB/SDM-RDFizer) engine and make them available through a Virtuoso Triple store: http://gtfs-bench.linkeddata.es/sparql. The data is organized as follows:

1. GTFS original (scale 1) in the GRAPH: http://gtfs1.linkeddata.es 
2. GTFS-5 (scale 5) in the GRAPH: http://gtfs5.linkeddata.es
3. GTFS-10 (scale 10) in the GRAPH: http://gtfs10.linkeddata.es
4. GTFS-50 (scale 50) in the GRAPH: http://gtfs50.linkeddata.es
5. GTFS-100 (scale 100) in the GRAPH: http://gtfs100.linkeddata.es
6. GTFS-500 (scale 500) in the GRAPH: http://gtfs500.linkeddata.es

If other scale value is selected to test the engine, the materialization can be obtained using any [RML-compliant](https://rml.io/implementation-report/) engine (we recommed SDM-RDFizer), the CSVs files exported by VIG and the gtfs-csv.rml.ttl mapping.

## Authors

- David Chaves-Fraga - [dchaves@fi.upm.es](mailto:dchaves@fi.upm.es)
- Freddy Priyatna
- Jhon Toledo
- Edna Ruckhaus
- Andrea Cimmino
- Oscar Corcho

Ontology Engineering Group, October 2019
