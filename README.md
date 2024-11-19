# XES to OCED-JSON to OCEDO

Cleaning up source code into readable documentation as Git code.

## Changelog


You can download the necessary input files for this project from the following link:
- [Download Input from Google Drive](https://drive.google.com/file/d/1itPGc6ZxQe0_UqYxgNZyBBc6CGtEOqY-/view?usp=sharing)
- [Download Files from Google Drive](https://drive.google.com/file/d/1dSNxCF3qN_sibZcsCVn5Ng5VMStiSH4g/view?usp=drive_link)

1. Existing ipynb scripts with Minor changes
    * `1_xes_to_json.ipynb` (some modification)
    * `2_json_to_ttl.ipynb` (some modification and splits)

2. Restructure files and folders
    * `files` contains the files needed to do the transformation, including RML mapping, oced (core) ontology, and csv files needed for enhancing the TTL files
    * `input` contains the input and output of the processes; I store the results and original xes files from all BPIC2015 1 to 5.
3. Updating the RML mappings for JSON to TTL
    * Based on our (latest) discussion, an update to the generic ontology is needed;`files/oced_ontology_VERSION4_FJE.ttl`.
    * Accordingly, I have to update the RML mapping file `files/rml_Me.ttl`.
4. Development of 3rd script for enhancing the TTL file with domain knowledge
    * To generate these enhancements, I used two SPARQL construct template, one for updating EVENT-OBJECT relations, and another for OBJECT-OBJECT relations.
    * The 3rd script will use these templates to "produce" new triples accordingly.  
    * for EVENT-OBJECT relations, an accompanying csv file (`files/2013_event-object_mapping.csv`), providing the information about "object_type,ocedd_class,ocedd_relation" is needed. it will add new relations based on the EVENT-OBJECT instances. 
    * for OBJECT-OBJECT relations, an accompanying csv file (`files/2013_object-object_mapping.csv`), providing the information about "object1_class,object2_class,object1_type,object2_type,ocedd_relation" is needed. it will add new relations based on the OBJECT-OBJECT instances. 
    * The enhanced TTL result (also integrating the ontology and the original TTL file) is stored as `input/2013_full-integrated.ttl` and ready to be given to the users :).
