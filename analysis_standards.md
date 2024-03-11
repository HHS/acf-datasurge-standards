# Analysis Standards

## Extract
This module should extract the data from its raw source and place the data in the input location. If there is no extraction necessary, then make a copy of the raw data and place in the input location. This step prevents corruption of the raw data and lessens the chance that we will have to reach out to our client for a second data delivery due to a mistake on our end.

## Initial data validation and exploration
This module ensures that all of the variables we expect are on the file, that variables have the type we expect (or we are able to convert to the types desired), that we understand what all of the variables mean, and that we have all of the records expected. These items should be verified assertively. In the event that any of these checks fail, an internal review is necessary to ensure that we are able to recover the information needed for analysis in spite of the failure. At this stage, it is also useful to determine if there are any unusual data patterns. If there are, we should inquire about them with the client.

## Data cleaning, transformation, and standardization
This module should execute all data cleaning, transformation, and standardization steps. For example, if data vary on some dimension (e.g., a survey changes slightly every year, or data from different organizations adopt different structures) the files output from this process should be standardized such that they can easily be merged or appended. To ensure all staff are aligned, a set of specifications defining the expected output at this step should be developed and stored in a central location. (This central location could be GitHub, but project leads should take care to omit any files that may contain PII or information which is not public from GitHub.) The specs should minimally include:

- A comprehensive list of variables to include on the file.
    - Types, labels (as needed), and valid ranges (as avaialable).
- A running list of business rules. For example, when missing values are encountered how will they be handled?
- Unique identifiers.
    - A combination of variables that should uniquely identify a row.
- Output type.
    - Will the file be saved as CSV, XLSX, RDS, DTA, JSON, in a SQL table, or in some other way?

## Post-cleaning data validation
Since files at this point should be standardized, a single module should validate that files are appropriately structured at this point.

## Prepare cleaned data for analysis
Could be superfluous, but may be useful if analyses are unclear or subject to change at the time of data cleaning.

## Analysis
Done iteratively with above 
