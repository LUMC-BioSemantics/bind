## Molecular outcome

### Semantic model figure
This module describes the __molecular__ data elements for therapeutic outcome. It specifically covers the data elements in the table that refer to the _Dystrophin restoration_. This module is based on the EJP RD CDE semantic model module for _DCDE Laboratory measurement_ group [CDE-semantic-model/DCDE_Laboratory_measurement](https://github.com/ejp-rd-vp/CDE-semantic-model/blob/develop/docs/DCDE_lab_measurement.md).
<p align="center">
    <a href="../images/rdf/molecular_outcome.png" target="_blank">
        <img src="../images/rdf/molecular_outcome.png">
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

:identifier_ a obo:IAO_0020000, sio:SIO_000115 ;
    rdfs:label "Identifier"^^xsd:string ;
    sio:SIO_000300 "AS-07 T2"^^xsd:string ;
    sio:SIO_000020 :treated_role_ .

:entity_ a obo:NCBITaxon_10090, sio:SIO_010375 ;
    rdfs:label "Entity: Mouse"^^xsd:string ;
    sio:SIO_000008 :genotype_ ;
    sio:SIO_000008 :treated_age_ ;
    sio:SIO_000228 :treated_role_ ;
    sio:SIO_000008 :treated_attribute_ .

:genotype_ a obo:SO_0001027, sio:SIO_000614 ;
    rdfs:label "Genotype"^^xsd:string ;
    sio:SIO_000300 "Mdx52"^^xsd:string .

:treated_age_ a obo:NCIT_C124440, sio:SIO_000614 ;
    rdfs:label "Age at treatment"^^xsd:string ;
    sio:SIO_000300 "7"^^xsd:integer ;
    sio:SIO_000221 :treated_age_unit_ .

:treated_age_unit_ a obo:UO_0000034, sio:SIO_000074 ;
    rdfs:label "Unit: Week"^^xsd:string .

:treated_role_ a obo:OBI_0000813, sio:SIO_000016 ;
    rdfs:label "Role: Treated"^^xsd:string ;
    sio:SIO_000356 :restoration_measurement_process_ .

:restoration_measurement_process_ a obo:ERO_0000833, obo:OBI_0000070, sio:SIO_000006 ;
    rdfs:label "Process: Measuring restored isoform"^^xsd:string ;
    sio:SIO_000291 :treated_target_ ;
    sio:SIO_000229 :restoration_output_ ;
    sio:SIO_000008 :measurement_time_ .

:treated_target_ a obo:UBERON_0002037, obo:UBERON_0002616, sio:SIO_010046 ;
    rdfs:label "Target: Anatomy"^^xsd:string ;
    sio:SIO_000068 :entity_ .

:restoration_output_ a obo:IAO_0000109, sio:SIO_000015 ;
    rdfs:label "Output: Restoration percent"^^xsd:string ;
    sio:SIO_000300 "4.5"^^xsd:float ;
    sio:SIO_000221 :output_unit_ ;
    sio:SIO_000628 :treated_attribute_ .

:measurement_time_ a obo:EUPATH_0023051, obo:IAO_0000582, sio:SIO_000417 ;
    rdfs:label "Timestamp: treatment start time"^^xsd:string ;
    rdfs:comment "Time post-injection"^^xsd:string ;
    sio:SIO_000300 "11"^^xsd:integer ;
    sio:SIO_000221 :time_unit_ ;
    sio:SIO_000001 :treated_role_ .

:output_unit_ a obo:UO_0000187, sio:SIO_000074 ;
    rdfs:label "Unit: %"^^xsd:string .

:treated_attribute_ a obo:PR_P11531-1, sio:SIO_000614 ;
    rdfs:label "Attribute: Dystrophin isoform"^^xsd:string ;
    sio:SIO_010079 <https://identifiers.org/MGI:94909> .

:time_unit_ a obo:UO_0000034, sio:SIO_000074 ;
    rdfs:label "Unit: Week"^^xsd:string .

<https://identifiers.org/MGI:94909> a <http://www.orpha.net/ORDO/Orphanet_121117>, obo:SO_0000704, sio:SIO_010035 ;
    rdfs:label "Gene: Dmd"^^xsd:string .
```

***
### Validation artifacts
##### ShEx figure
<p align="center">
    <a href="../images/shex/molecular_outcome.svg" target="_blank">
        <img src="../images/shex/molecular_outcome.svg">
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
    a [obo:IAO_0020000] ;
    a [sio:SIO_000115] ;
    rdfs:label xsd:string? ;
    sio:SIO_000300 xsd:string ;
    sio:SIO_000020 @:treatedRoleShape
}

:entityShape IRI {
    a [obo:NCBITaxon_10090] ;
    a [sio:SIO_010375] ;
    rdfs:label xsd:string? ;
    sio:SIO_000008 @:genotypeShape ;
    sio:SIO_000008 @:treatedAgeShape ;
    sio:SIO_000228 @:treatedRoleShape ;
    sio:SIO_000008 @:treatedAttributeShape
}

:genotypeShape IRI {
    a [obo:SO_0001027] ;
    a [sio:SIO_000614] ;
    rdfs:label xsd:string? ;
    sio:SIO_000300 xsd:string
}

:treatedAgeShape IRI {
    a [obo:NCIT_C124440] ;
    a [sio:SIO_000614] ;
    rdfs:label xsd:string? ;
    sio:SIO_000300 xsd:integer ;
    sio:SIO_000221 @:treatedAgeUnitShape
}

:treatedAgeUnitShape IRI {
    a [obo:UO_0000034] ;
    a [sio:SIO_000074] ;
    rdfs:label xsd:string?
}

:treatedRoleShape IRI {
    a [obo:OBI_0000813] ;
    a [sio:SIO_000016] ;
    rdfs:label xsd:string? ;
    sio:SIO_000356 @:restorationMeasurementProcessShape
}

:restorationMeasurementProcessShape IRI {
    a [obo:ERO_0000833] ;
    a [obo:OBI_0000070] ;
    a [sio:SIO_000006] ;
    rdfs:label xsd:string? ;
    sio:SIO_000291 @:treatedTargetShape ;
    sio:SIO_000229 @:restorationOutputShape ;
    sio:SIO_000008 @:measurementTimeShape
}

:treatedTargetShape IRI {
    a [obo:UBERON_0002037] ;
    a [obo:UBERON_0002616] ;
    a [sio:SIO_010046] ;
    rdfs:label xsd:string? ;
    sio:SIO_000068 @:entityShape
}

:restorationOutputShape IRI {
    a [obo:IAO_0000109] ;
    a [sio:SIO_000015] ;
    rdfs:label xsd:string? ;
    sio:SIO_000300 xsd:float ;
    sio:SIO_000221 @:outputUnitShape ;
    sio:SIO_000628 @:treatedAttributeShape
}

:measurementTimeShape IRI {
    a [obo:EUPATH_0023051] ;
    a [obo:IAO_0000582] ;
    a [sio:SIO_000417] ;
    rdfs:label xsd:string? ;
    rdfs:comment xsd:string ;
    sio:SIO_000300 xsd:integer ;
    sio:SIO_000221 @:timeUnitShape ;
    sio:SIO_000001 @:treatedRoleShape
}

:outputUnitShape IRI {
    a [obo:UO_0000187] ;
    a [sio:SIO_000074] ;
    rdfs:label xsd:string?
}

:treatedAttributeShape IRI {
    a [obo:PR_P11531-1] ;
    a [sio:SIO_000614] ;
    rdfs:label xsd:string? ;
    sio:SIO_010079 @:geneShape
}

:timeUnitShape IRI {
    a [obo:UO_0000034] ;
    a [sio:SIO_000074] ;
    rdfs:label xsd:string?
}

:geneShape IRI {
    a [<http://www.orpha.net/ORDO/Orphanet_121117>] ;
    a [obo:SO_0000704] ;
    a [sio:SIO_010035] ;
    rdfs:label xsd:string?
}
```
