# Scripts

## File Naming

Names should be human-readable, machine-readable, and sortable. 

### Human-readable

File names should be easy to understand and self-explanatory. They should be both concise and descriptive enough that people can make a reasonable guess about what the file contains or its role in the analysis. File names should take into account the context of surrounding organizating structures, e.g. repository and directory names, to avoid redundancy. For example, within a repository named `ohs_pir_pipeline`, a file with code for ingesting raw reports should be named `ingest_raw_reports.R` rather than `ingest_raw_ohs_pir_reports_for_pipeline.R`. Use consistent naming conventions throughout the scripts/codebase to maintain uniformity.

### Machine-readable

When naming things, avoid spaces and special characters. Use "_" as a separator instead of spaces.

### Sortable

- Names should be structured to allow for sorting when relevant, i.e., if chronological or ordering affects the file or a group of files.
- If there is a sequential order of the files, like a processing pipeline, its order should be built into their file names.
    - Example:
        - `01_file_processes.R`
        - `02_summarize_transaction.R`
        - `03_postprocess_data.R`
        - `04_bi_tool_data.R`
- If there is a chronological ordering, ordering should be built into file names.
    - Example:
        - `2021_survey_data.py`
        - `2022_survey_data.py`
        - `2023_survey_data.py`
- If files contain a date component, use the format: YYYYMMDD for year, month and day format.
    - Example:
        - `decision_book_20231228.csv`
- Version numbers should be avoided in file naming.
- Abbreviations and acronyms should be avoided. While a limited use of abbreviations may be acceptable, it is generally better to use descriptive and clear names instead. That will help improve script/code readability and understanding.   

## Function/Class/Variable Naming

### Case conventions

Within a single language, follow camelCase or snake_case:

- For Python, use snake_case per [Python convention](https://peps.python.org/pep-0008/)
- For R, use snake_case per [Tidyverse convention](https://style.tidyverse.org/syntax.html)
- For SQL, use snake_case and apply the following [style guide](https://github.com/janejuenyang/welcome/blob/main/guides/sql_guide.md)
- For Java, use camelCase per [Java convention](https://www.javatpoint.com/camel-case-in-java)

camelCase naming: 
- start with a lowercase letter and capitalize the first letter of each subsequent word, e.g., getUserData()
     
snake_case naming: 
- Use all lowercase letters, numbers, and "_" as separator.
     - Examples:       
          - `02_ohs_comments_ingestion.py`
          - `get_medicare_data.R`
              
Additional style standards for SQL naming:
- Use all lowercase for field names.
- Use uppercase for SQL function names.
- Use the 'AS' keyword when aliasing a field or table.
- Be as descriptive as possible with 'CTE' names.
- Avoid single-letter aliases, e.g., c1, c2. If names are getting too long, prefer shortened tables names, e.g., cust for customers.

### Declarative naming

- Like with files, names within a script should be human-readable and machine-readable. Choose self-explanatory names, e.g. a function `add_row()` tells that this function will add a row; a variable `df_cases` is a dataframe of case management records.
- Names should be as concise as possible while maintaining clarity, so that they are simple to type and easy to remember

#### Functions

- Use verbs for function names if the function changes or evaluates an object:
    - Examples:
        - `add_row()`
        - `sort_order()`
        - `is_true()`
- Use nouns for function names if they are used to return a certain value:
    - Examples:
        - `manhattan_distance()`
        - `success_ratio()`
      
#### Variables

- Use prefixes to indicate what the variable refers to, e.g.
     - `df_` for dataframes
     - `g_` for graphs
     - `p_` for a parameter
