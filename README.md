# seva-hadatac-data-template

## Introduction
This repository serves as a template for easily creating complex studies for ingestion into hadatac and SEVA.

## Requirements
- [Python 3](https://www.python.org/downloads/)
- [Requests](https://requests.readthedocs.io/en/master/)
- [openpyxl](https://openpyxl.readthedocs.io/en/stable/)

## Getting Started
1. Click the green "Use this template" button. Name your repository, decide if you would like it to be public or private, and then click "Create repository from template".
2. Clone your new repository as you normally would.
    - Example: `git clone git@github.com:Jamesm4/template-test.git` where "Jamesm4" is my username, and "template-test" is the name of my repository.
3. Fill out instruments.csv, replacing the examples with your instruments. The format is "instrumentName,platformName".
    - For large studies its probably best to create a script for this process, as well as the other csv files. This is beyond the scope of this tutorial, but feel free to use whatever langauge or method you prefer.
4. Fill out detectors.csv, replacing the examples with your detectors. The format is "detectorName,instrumentName".
    - The instrument names must match the instrument names in instruments.csv
5. Fill out identifiers.csv, matching up the detectors with an ontology class that represents the detector, and a unit class. The format is "detectorName,identifier,unit"
    - A short name is used for the identifier. For example, for the uri https://semanticscience.org/resource/SIO_000367.rdf, you would shorten this name to SIO:000367. Hadatac keeps track of the base uri and will expand the uri for you.
    - The same applies for units. One of the best ontologies for finding units is the [Unit Ontology](http://www.ontobee.org/ontology/UO)
6. Run makeMetadata.py, giving your study name and email address as command line arguments. `python makeMetadata.py "Your Study name" jsmith@example.com`.
    - The email address must be registered with hadatac for your data to be ingested.
7. Open the generated STD file, "STD-Your_Study_Name.xlsx", and fill out the remaining information.
8. Create your data acquisition files.
    - You will need one DA file per instrument.
    - File names must be named "DA-Your_Study_Name-instrumentName.xlsx"
    - The first row will be something like "timestamp,detector1,detector2,detector3"
    - The remaining rows will be your data.
    - Timestamps must be in ISO 8601 format. Ex: "2020-12-25T17:00:00.000Z"
9. Preview your files, and then you're ready to begin testing ingestion in hadatac.
    
