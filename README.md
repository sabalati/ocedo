# XES to OCED-JSON to OCEDO

Cleaning up source code into readable documentation as Git code.

## Changelog


You can download the necessary input files for this project from the following link:
- [Download Input from Google Drive](https://drive.google.com/file/d/1itPGc6ZxQe0_UqYxgNZyBBc6CGtEOqY-/view?usp=sharing)
- [Download Files from Google Drive](https://drive.google.com/file/d/1dSNxCF3qN_sibZcsCVn5Ng5VMStiSH4g/view?usp=drive_link)

1. Renaming existing ipynb scripts
    * `XES to JSON v4.1 Maxim.ipynb` ==> `1_xes_to_json.ipynb` (no changes)
    * `rml.ipynb` ==> `2_json_to_ttl.ipynb` (some modification and splits)

2. Restructure files and folders
    * `doc` contains the (old) figures on the BPIC 2013 structure, BPIC_2013 info document, and the `bpic_2013_spec.txt`, detailing the generic ontology (namespace: "ocedo") used and the _extension_ specific for BPIC_2013 (namespce: "ocedd")
    * `files` contains the files needed to do the transformation, including RML mapping, oced (core) ontology, and csv files needed for enhancing the TTL files
    * `input` contains the input and output of the processes; I only store the results from small xes (`2013_small.xes`), but not the big one (`2013_full.xes`). 
3. Updating the RML mappings for JSON to TTL
    * Based on our (latest) discussion, an update to the generic ontology is needed; some documentation about it is available on the `doc/bpic_2013_spec.txt` (GENERIC-ontology 3.0) and the ontology file is available at `files/oced-ontology.ttl`.
    * Accordingly, I have to update the RML mapping file `files/rml_mapping.ttl`.
    * Furthermore, since the original JSON file produced from 1st script is not suitable for RML mapping, some modification is needed before transforming into TTL; therefore, a temp file called `files/2013_small-mod.json` is produced and used as input for the TTL generation in 2nd script.
    * The result of "raw" transformation is available as `files/2013_small.ttl`.
4. Development of 3rd script for enhancing the TTL file with domain knowledge
    * After reading the spec (PDF file inside `doc` folder), I came up with ideas about how the domain knowledge would look like, which is briefly written in `doc/bpic_2013_spec.txt` (BPIC 2013 specific). 
    * To generate these enhancements, I used two SPARQL construct template, one for updating EVENT-OBJECT relations, and another for OBJECT-OBJECT relations.
    * The 3rd script will use these templates to "produce" new triples accordingly.  
    * for EVENT-OBJECT relations, an accompanying csv file (`files/2013_event-object_mapping.csv`), providing the information about "object_type,ocedd_class,ocedd_relation" is needed. it will add new relations based on the EVENT-OBJECT instances. 
    * for OBJECT-OBJECT relations, an accompanying csv file (`files/2013_object-object_mapping.csv`), providing the information about "object1_class,object2_class,object1_type,object2_type,ocedd_relation" is needed. it will add new relations based on the OBJECT-OBJECT instances. 
    * The enhanced TTL result (integrating also the ontology and the original TTL file) is stored as `input/2013_small-integrated.ttl` and ready to be given to the users :).
