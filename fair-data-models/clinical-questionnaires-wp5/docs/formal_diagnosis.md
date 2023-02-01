## Formal Diagnosis

### Semantic model figure
This module describes the data elements in the KHTQ. It specifically covers the section part in the questionnaire _FORMAL DIAGNOSIS_. This module is based on the EJP RD CDE semantic model module for _Diagnosis_ group [CDE-semantic-model/personal information](https://github.com/ejp-rd-vp/CDE-semantic-model/blob/980b1125222f1654c03da605835cbfd987d7970e/docs/personal_information.md).
<p align="center">
    <a href="../images/rdf/formal_diagnosis.png" target="_blank">
        <img src="../images/rdf/formal_diagnosis.png">
    </a>
</p>

***

### Example RDF (turtle)
```ttl
@prefix : <http://w3id.org/bind/data/v1/example-rdf/> .
@prefix obo: <http://purl.obolibrary.org/obo/> .
@prefix sio: <http://semanticscience.org/resource/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

:identifier_ a sio:SIO_000115 ;
    rdfs:label "Identifier"^^xsd:string ;
    sio:SIO_000020 :patient_role_ ;
    sio:SIO_000300 "uid_000001"^^xsd:string .

:person_ a sio:SIO_000498 ;
    rdfs:label "Person"^^xsd:string ;
    sio:SIO_000228 :patient_role_ ;
    sio:SIO_000008 :formal_diagnosis_attribute_ .

:patient_role_ a obo:OBI_0000093, sio:SIO_000016 ;
    rdfs:label "Role: Patient"^^xsd:string ;
    sio:SIO_000356 :formal_diagnosis_process_ .

:formal_diagnosis_process_ a sio:SIO_000006, sio:SIO_001022 ;
    rdfs:label "Process: Formal medical diagnosis"^^xsd:string ;
    sio:SIO_000230 :test_input_ ;
    sio:SIO_000229 :formal_diagnosis_output_ .

:formal_diagnosis_output_ a sio:SIO_000015, sio:SIO_001003, sio:SIO_000785 ;
    rdfs:label "Output Type: Formal medical diagnosis"^^xsd:string ;
    sio:SIO_000300 "Yes"^^xsd:string ;
    sio:SIO_000628 :formal_diagnosis_attribute_ .

:formal_diagnosis_attribute_ a sio:SIO_000614, sio:SIO_010299 ;
    rdfs:label "Attribute Type: Disease"^^xsd:string .

:test_input_ a obo:NCIT_C17048, sio:SIO_000148 ;
    rdfs:label "Input Type: KHTQ Questionnaire Document"^^xsd:string ;
    sio:SIO_000028 :test_input_question_ .

:test_input_question_ a sio:SIO_000085, sio:SIO_000015 ;
    rdfs:label "Part Type: Question"^^xsd:string ;
    sio:SIO_000300 "Autism Spectrum Disorder (ASD)"^^xsd:string ;
    sio:SIO_000332 obo:MONDO_0005258 .
```

***
### Validation artifacts
##### ShEx figure
<p align="center">
    <a href="../images/shex/formal_diagnosis.svg" target="_blank">
        <img src="../images/shex/formal_diagnosis.svg">
    </a>
</p>

***
##### ShEx
``` ShEx
PREFIX : <http://w3id.org/bind/data/v1/shex/>
PREFIX obo: <http://purl.obolibrary.org/obo/> 
PREFIX sio: <http://semanticscience.org/resource/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

:identifierShape IRI {
    a [sio:SIO_000115] ;
    rdfs:label xsd:string? ;
    sio:SIO_000020 @:patientRoleShape ;
    sio:SIO_000300 xsd:string
}

:personShape IRI { 
    a [sio:SIO_000498] ;
    rdfs:label xsd:string? ;
    sio:SIO_000228 @:patientRoleShape ;
    sio:SIO_000008 @:formalDiagnosisAttributeShape
}

:patientRoleShape IRI {
    a [sio:SIO_000016] ;
    a [obo:OBI_0000093] ;
    rdfs:label xsd:string? ;
    sio:SIO_000356 @:formalDiagnosisProcessShape
}

:formalDiagnosisProcessShape IRI {
    a [sio:SIO_000006] ;
    a [sio:SIO_001022] ;
    rdfs:label xsd:string? ;
    sio:SIO_000230 @:testInputShape ;
    sio:SIO_000229 @:formalDiagnosisOutputShape
}

:formalDiagnosisOutputShape IRI {
    a [sio:SIO_000015] ;
    a [sio:SIO_001003] ;
    a [sio:SIO_000785] ;
    rdfs:label xsd:string? ;
    sio:SIO_000300 xsd:string ;
    sio:SIO_000628 @:formalDiagnosisAttributeShape
}

:formalDiagnosisAttributeShape IRI {
    a [sio:SIO_000614] ;
    a [sio:SIO_010299] ;
    rdfs:label xsd:string?
}

:testInputShape IRI {
    a [sio:SIO_000148];
    a [obo:NCIT_C17048] ;
    rdfs:label xsd:string? ;
    sio:SIO_000028 @:testInputQuestionShape
}

:testInputQuestionShape IRI {
    a [sio:SIO_000015] ;
    a [sio:SIO_000085] ;
    rdfs:label xsd:string? ;
    sio:SIO_000300 xsd:string ;
    sio:SIO_000332 IRI /^http:\/\/purl.obolibrary.org\/obo\/MONDO_/
}
```
