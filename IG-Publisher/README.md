# HCX FHIR IG PUBLISHER

This document details about the setup of HCX FHIR IG Publisher.

## Prerequisite
* Install Above Java 8 Version
* Install the `ruby` to install `jekyll` plugin
* Install the `jekyll` from here  https://jekyllrb.com/docs/installation/
* Download the latest IG publisher Jar file from here
     https://github.com/HL7/fhir-ig-publisher/releases



## Initial setup

* Create A root directory for the overall project, `IG-Publisher` in this case.

* With in the `IG-Publisher` Create a `Input` Directory and place all required FHIR definiations 

* The FHIR Definiation file name should be `$resourceType-$identifier.json`

* Create the ig.json ImplementationGuide instance
  * Place this file in the `input` directory.
  * Setup your IDE to support JSON Schema support to help with this step and later ones.
  * Name can be changed.
  * Define all the definition in the `resource` part of `definition` exmaple are here - 
  ```
  {
        "extension": [
          {
            "url": "http://hl7.org/fhir/tools/StructureDefinition/Patient",
            "valueString": "SearchParameter"
          }
        ],
        "reference": {
          "reference": "StructureDefinition/Patient"
        },
        "name": "HCX Patient",
        "description": "**Search by subject - a patient**  \n**NOTE**: This US Core SearchParameter definition extends the usage context of the\n[Conformance expectation extension](http://hl7.org/fhir/R4/extension-capabilitystatement-expectation.html)\n - multipleAnd\n - multipleOr\n - comparator\n - modifier\n - chain",
        "exampleBoolean": false
      }

  ```
  For more details of IG please check this link - https://www.hl7.org/fhir/implementationguide.html

* Create the `ig.ini` publisher configuration file.
  * Name and directory can be changed but its location sets the root/working directory for the publisher tool.
  * The location of this file is considered to be the root of the IG working directory, `IG-Publisher` in this example.
  * Other relative content/paths are relative to the location of this file.


## Template Creation

FHIR by default provides few templates, Where we can use those default template to render the definiations.

Default Templates - 

    1. fhir.base.template
    2. hl7.base.template
    3. hl7.fhir.template
    4. hl7.davinci.template	
    5. hl7.cda.template	

for more details of using the default templates you can refer this link - https://build.fhir.org/ig/teryfly/ig-guidance/

### How to create Custom Template ?

FHIR IG Publisher provides a capabality to create a custom template as well. 

1. Download any default template and rename the folder since while executing, the publisher will place all template related information into `template` folder. in my case i have renamed it to `hcx-ig-template-local`

2. Inside the `hcx-ig-template-local` create pacakge folder and within it create an `package.json` and add all template related meta information into the package.json

```
{
    "name": "hcx-ig-template-local",
    "version": "0.1.0",
    "type": "fhir.template",
    "license": "",
    "description": "HCX FHIR Template",
    "author": "Manjunath Davanam",
    "canonical": "",
    "base": "fhir.base.template",
    "dependencies": {
        "fhir.base.template": "current"
    }
}

```

3. Define this tempalte name in the `ig.ini` file

    ```
    template = hcx-ig-template-local
    ```


## How to Run the IG Publisher Locally 

Command - 
```
 java -jar ./publisher.jar -ig ig.ini

```


While running you should able to see some certian logs related to loadign the template, and rending the FHIR definiations. 




