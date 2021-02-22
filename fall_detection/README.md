# Adaptive and personalized carepath management to solve a detected fall event


## Introduction
This demonstration shows that based on the semantic representation of resources, the weighted state transition logic is able to generate adaptive and personlized paths as guidance to resolve a detected fall event.

Following the concepts defined in our paper, the semantic repsentation of resources is an example of the decriptive intelligence, that is the ability to acquire the awareness of the current status, by aggregate and understand data from different resources. Knowledges of the relevant domains are expressed as inference rules to deduce new information, as an exmaple or predictive intelligence. The adaptive path generation at different time frames is an example of the prescriptive intelligence, that is the ability to guide the response based on awareness of current state and the predicted states.

This demonstration contains four scenarios:

- Scenario A demonstrates the generation of paths to solve a fall event at different time frames following the update of the context status, the generated paths are following the workflow specified in Figure 1.
- Scenario B demonstrates that when diagnosis information from Electronic Healthcare Record (EHR) and relevant clinical knowledge is provided, the system is able to take such information into account and produce more appropriate paths.
- Scenario C demonstrates that when there is semantic gap between the provided EHR data and clinical knowledge, the system is not able to well utilize the available information.
- Scenario D demonstrates that by introducing terminology mapping to build common semantic, the system is able to well utilize the available information.

**Please open the file aal_demo_fall_detection.ipynb to view a detailed demonstration of the four scenarios.** <br>
It is also possible to run the entire demo in this notebook after installing the EYE resoner (https://github.com/josd/eye)

## Folders and files

**data** <br>
*This folder contains the data required for this scenario, provided by different sources, and represented in the semantic web language RDF/Turtle:* <br>
- basic_information.ttl - provide basic, including information of the patient, healthare providers, their relations, etc.
- data_t0.ttl - patient status at t0, that a fall event is detected
- data_t1.ttl - patient status at t1, that a fall event is confirmed
- data_t2.ttl - patient status at t2, that non medical assistance is required.
- ehr_icd10.ttl - simplified electronic healthcare record of the patient, containing a disease coded in ICD 10
- ehr_snomed.ttl - simplified electronic healthcare record of the patient, containing two diseases coded in SNOMEDCT

By choosing between data_t0, data_t1, data_t2, we mimic the different status of the patient over three different time frames.<br>
By choosing between ehr_icd10 and ehr_snomed, we mimic EHR of a patient in different healthcare systems.<br>

**knowledge** <br>
*This folder contains the knowledge used in this scenario, covering different domains, and represented in semantic web language N3*<br>
- aal_knowledge.n3 - knowledge of the AAL domain, to infer two person is related based on stated relations.
- clinical_knowledge.n3 - knowledge of the clinical domain, to infer lower leg fracture is also a bone fracture, and if a patient with bone fracture has a fall event confirmed, that person needs ambulance.
- service_descriptions.n3 - descriptions of a set of services, such as to confirm if it is a fall event, schedule an ambulance. 
- terminology_mapping.n3 - a sample case of terminology mapping between ICD 10 and SNOMED CT, using SKOS ontology.<br>

**path** <br>
*This folder contains the paths generated at the different stages*

**path_engine.n3** <br>
*This file is the weighted state transition engine implemented by Jos De Roo and Hong Sun*

**goal.n3q** <br>
*This file specifies the target state to reach, that is to resolve the detected fall event*
