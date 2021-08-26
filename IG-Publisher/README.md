# HCX FHIR IG PUBLISHER

This document details about the setup of HCX FHIR IG Publisher.

## Initial setup
* Create A root directory for the overall project, `IG-Publisher` in this case.
* With in the `IG-Publisher` Create a Input Directory and place all required FHIR definiations 

* The FHIR Definiation file name should be `$resourceType-$identifier.json`

* Download the latest IG publisher Jar file from here
     https://github.com/HL7/fhir-ig-publisher/releases

* Install Above Java 8 Version

* Install the `jekyll` from here  https://jekyllrb.com/docs/installation/

* `jekyll` It takes text written in your favorite markup language and uses layouts to create a static website.

* Create the ig.json ImplementationGuide instance
  * Place this file in the `input` directory.
  * Setup your IDE to support JSON Schema support to help with this step and later ones.
  * Name can be changed.

* Create the ig.ini publisher configuration file.
  * Name and directory can be changed but its location sets the root/working directory for the publisher tool.
  * The location of this file is considered to be the root of the IG working directory, `IG-Publisher` in this example.
  * Other relative content/paths are relative to the location of this file.  


