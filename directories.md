# Directories

## Directory Naming

- Directory names should be both machine and human readable. 
- Consider including the client name or abbreviation in the top level project directory name, when possible.
- Use _ the folder name into components. Avoid special characters, as they can cause errors or compatibility issues.
- Name folders to reflect their content. Avoid including team names, as they may change.
- Be specific to differentiate between similar projects/categories.
- Use leading zeros for sequential numbering, when needed (e.g., “01”).
- Prefer lowercase for directory names.

## Directory Structure

A good folder structure should be hierarchical, modular, and scalable, and avoid nesting too many subfolders or creating duplicates. Adopt the following standards when setting up the initial directory structure.

- Main Directory: Start with a main directory for the project.
- Common Subdirectories: Within a project directory, general folders include:
    - /input
        - Contains datasets relevant to the project.
    - /intermediate
        - Contains intermediate outputs for analyses etc.
    - /output
        - Contains visuals, graphs, tables, datasets or other outputs derived from code.
    - /_archive
        - Contains older versions of code no longer needed or in use.
    - /code
        - Contains all code to generate desired results and outputs.
        - If the /code contains many scripts and/or these scripts are written in multiple languages, consider including subdirectories by language or technology such as:
            - /python
            - /sql
    - Further subdirectories may be necessary, especially in language-specific directories such as:
        - /r/utils
        - /sql/views 
    - /test
        - Directory for testing code.
        - This directory may need to be moved into another directory (e.g. the code directory) depending upon the project.

## File Organization

- Separate Files by Functionality: Keep related files together within directories to improve readability and maintainability.
- Avoid Large Directories: If a directory becomes too large, consider further subdivision or refactoring to improve navigation.
- Version Control Files: Include version control files like .gitignore and .gitkeep to manage versioning and ignore unnecessary files.

## Dependency Management

- Separate Dependency Directories: Keep dependencies separate from the main codebase, especially for larger projects.
- Use Package Managers: Utilize package managers (e.g., pip for Python, npm for JavaScript) to manage dependencies efficiently.
- Document Dependencies: Document external dependencies and their versions in a requirements.txt, package.json, or equivalent file.

## Build and Configuration Files

- Configuration Directories: Keep configuration files separate from source code (e.g., Config/, Settings/).
- Standardize Configuration Names: Follow a consistent naming convention for configuration files to improve readability and maintainability.

## Continuous Integration and Deployment (CI/CD)

- CI/CD Configuration: Include files for CI/CD workflows (e.g., .gitlab-ci.yml, .github/workflows/) in the root directory or a dedicated CI/CD directory.

## Other Considerations

- Renaming directory names can have adverse consequences, e.g., breaking downstream links.
- Keep in mind that file paths cannot extend beyond certain limits:
- SharePoint/OneDrive path limit is 400 characters.
- Windows path limit is 260 characters.