# Analysis Standards

The kinds of analyses that the ACF Data Surge Team will engage in can take on a wide range of scopes and levels of complexity. Therefore this guide makes few specific recommendations about exactly what to include in code produced on an analysis project. Instead, this page provides a high-level overview of the components central to a well-executed analysis project:

- [Extraction](#extract)
- [Initial data validation](#initial-data-validation-and-exploration)
- [Data cleaning, transformation, and standardization](#data-cleaning-transformation-and-standardization)
- [Post-cleaning data validation/diagnostics](#post-cleaning-data-validation)
- [Analysis preparation (optional)](#analysis-preparation)
- [Analysis](#analysis)
- [Output](#outputs)

Throughout this page we refer to a module. In Python, a module is essentially any script with the ".py" extension. These scripts can have function, variable, and class definitions which can be imported into other modules. We adopt this Python definition of a module to apply to any language an analysis project is being conducted in. While the text in a given section may refer to a single module, we anticipate that there will be definitions imported from elsewhere that are necessary for this single module to run.

## Extract
This module should extract the data from its raw source and place the data in the input location. If there is no extraction necessary, then make a copy of the raw data and place in the input location. This step prevents corruption of the raw data and lessens the chance that we will have to reach out to our client for a second data delivery due to a mistake on our end.

## Initial data validation and exploration
This module ensures that all of the variables we expect are on the file, that variables have the type we expect (or we are able to convert to the types desired), that we understand what all of the variables mean, and that we have all of the records expected. These items should be verified assertively. In the event that any of these checks fail, an internal review is necessary to ensure that we are able to recover the information needed for analysis in spite of the failure. At this stage, it is also useful to determine if there are any unusual data patterns. If data are not recoverable or unusual patterns are present in the data, inquire about them with the client.

The initial data validation and exploration step is a good use case for [notebooks](notebooks.md) (i.e. Quarto/Jupyter).

## Data cleaning, transformation, and standardization
This module executes data cleaning, transformation, and standardization steps. It is common for data to vary on some dimension (e.g., a survey changes slightly every year, or data from different organizations have different structures). The files output from this remove enough of this variation such that they can easily be merged (columns added) or appended (rows added). To ensure all developers are aligned, a set of specifications defining the expected output from data cleaning should be developed and stored in a central location. (This central location could be GitHub, but project leads should take care to omit any files that may contain PII or information which is not public from GitHub.) The specs should minimally include:

- A comprehensive list of variables to include on the file.
    - Types, labels (as needed), and valid ranges (as available).
- A running list of business rules. 
    - For example, when missing values are encountered how will they be handled?
- Unique identifiers.
    - A combination of variables that should uniquely identify a row.
- File output type.
    - CSV, XLSX, RDS, DTA, JSON, SQL table, etc.

## Post-cleaning data validation
This single module confirms that cleaned files are aligned with the specs. Single here means that the module is not survey, year, organization, district, etc. specific. The module should work when validating any data from produced by the cleaning module above. As with the pre-cleaning data validation, this module assertively validates the structure of post-cleaning data. Files which fail the validation should be returned to the developer who produced them for updates.

This module is a good place to insert any additional exploration steps desired before analysis. The module might produce correlations, graphs, and tables which can be checked to ensure that variable values are not only within the ranges expected and of the expected type, but that they make sense contextually.

As with the initial data validation, the post-cleaning validation module is a good use case for [notebooks](notebooks.md).

## Analysis preparation
Module(s) which create constructs or intermediate data files necessary for the proposed analyses can be developed ad-hoc. If there is only a single analysis or if the set of analyses to be performed is clear from the outset of the project, these modules may be unnecessary. In the event that they are needed, developers should validate the variables or files created by these modules as they would variables created before the post-cleaning validation. 

These modules should be separate from, but developed in concert with the analysis module(s) and are therefore likely to change throughout the analysis project.

## Analysis
Develop separate modules for each analysis, unless the analyses are intimately related. For example, several different regression model specifications using the same data and similar covariates can form a single module, but propensity score matching and clustering should be separate modules. Developing analyses is likely to require iteratively returning to the analysis preparation modules.

## Outputs
Finally, define a set of output modules to generate the desired outputs. These modules should be developed based on the specific requirements of the project and the intended audience of the analysis results.
