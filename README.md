# XES to OCED-JSON to OCEDO

Cleaning up source code into readable documentation as GitHub code.

## Changelog

1. Renaming existing ipynb scripts
    * `XES to JSON v4.1 Maxim.ipynb` ==> `1_xes_to_json.ipynb` (no changes)
    * `rml.ipynb` ==> `2_json_to_ttl.ipynb` (some modification and splits)

2. Restructure files and folders
    * `doc` contains the (old) figures on the BPIC 2013 structure, BPIC_2013 info document, and the `bpic_2013_spec.txt`, detailing the generic ontology (namespace: "ocedo") used and the _extension_ specific for BPIC_2013 (namespce: "ocedd")
    * `files` contains the files needed to do the transformation, including RML mapping, oced (core) ontology, and csv files needed for enhancing the TTL files
    * `input` contains the input and output of the processes; I only store the results from small xes (`2013_small.xes`), but not the big one (`2013_full.xes`). 
3. Updating the RML files for JSON to TTL
    * Based on our (latest) discussion, an update to the generic ontology is needed; some documentation about it is available on the `doc/bpic_2013_spec.txt` (GENERIC-ontology 3.0) and the ontology file is available at `files/oced-ontology.ttl`.
    * Accordingly, I have to update the RML mapping file `files/rml_mapping.ttl`.
    * Furthermore, since the original JSON file produced from 1st script is not suitable for RML mapping, some modification is needed before transforming into TTL; therefore, a temp file called `files/2013_small-mod.json` is produced and used as input for the TTL generation in 2nd script.
    * The result of "raw" transformation is available as `files/2013_small.ttl`.
4. Development of 3rd script for enhancing the TTL file with domain knowledge
    * 




