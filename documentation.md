# Comments and documentation

**Documentation Principles**:

- **Audience-Centric Writing**: Tailor content to the intended audience, considering their knowledge and interests.
- **Addressing both the 'Why' and the 'How'**: Explain the purpose behind actions, not just the steps.
- **Conciseness**: Cover all necessary information briefly, avoiding unnecessary elaboration
- **Logical Storage Location**: Store documents in easily accessible locations aligned with user preferences.

## Code-based Project

### Document Headers

- Include a clear and concise title that describes the purpose of the document.
- Provide information about the author(s) or creator(s) of the document.
- Include a brief description of the document's content and its intented audience.
- Optionally, include information about the version of the document and any relevant dates or revision history, similar to code standards.
    - Examples:
    ```
    #/*****************************************************************************************/
    #/ Date Created: "DATE"
    #/ Programmer: "PROGRAMMER NAME"
    #/ Project: "PROJECT NAME"
    #/ Purpose: "SHORT DESCRIPTION"
    #/ References: "LINKS OF WEBSITES OR CONFLUENCE PAGE"
    #/*****************************************************************************************/
    ```
### In-line Comments

- Use in-line comments only to explain complex or non-obvious sections of code.
- Keep comments concise and to the point, focusing on explaining "why" rather than "what" the code is doing (the "what" should ideally be self-explanatory from the code itself)
- Avoid unnecessary comments that simply restate what the code is doing unless it is truly necessary for clarity.
- Ensure comments are kept up-to-date with changes to the code.
- If using a notebook (e.g., .ipynb, .Rmd, .Qmd etc.), each cell can include a comment to provide context about what that part of script/cell does.
- Use consistent formating and style throughout scripts, following any established style guides or conventions.
    - Examples:
        - For R, follow the [Tidyverse style guide](https://style.tidyverse.org/documentation.html).
        - For Python, follow the [Python Enhancement Proposals (PEP) 8 style guide](https://peps.python.org/pep-0008/).
    
### README Files

- Provide a clear and descriptive title for the README file.
- Include an overview of the project, describing its purpose, goals, and any key features.
- Provide instructions for how to install, configure, and use the project or software.
- Include any prerequisites or dependencies required to run the project.
- Provide examples or usage scenarios to help users understand how to interact with the project.
- Include information about how to contribute to the project, if applicable.
- Use headings, bullet points, and formatting (such as bold or italic text) to make the document or README easier to read and navigate.
- Consider using markdown or another lightweight markup language for README files, since it allows for easy formatting and is widely supported on platforms like GitLab or GitHub.

### Hyperlinks

Accessible hypertext links can help to link the content to accessible web pages and documents. Follow the [How to create accessible hypertext links](https://www.nysed.gov/webaccess/create-accessible-hypertext-links) guideline:

- Use a concise description of the destination webpage for hyperlink text, e.g., don't use "click here" or "read more" as text for links, use "follow the [Tidyverse style guide](https://style.tidyverse.org/documentation.html)".
- Do not captialize all letters in links, e.g., should not use "GUIDELINE OF HYPERLINKS" for text.
- Avoid using URLs for link text, e.g., don't use "click [https://www.nysed.gov/webaccess/create-accessible-hypertext-links](https://www.nysed.gov/webaccess/create-accessible-hypertext-links) for guidelines for hyperlinks".
- Do not use the word 'link' as part of the link text, e.g., avoid using "follow [link](https://www.nysed.gov/webaccess/create-accessible-hypertext-links) for details of guidelines".
- Do not use tooltips/screentips to add additional information, e.g., should not use tooltips here "[Guideline](https://www.nysed.gov/webaccess/create-accessible-hypertext-links "Guildline of hyperlinks")".
- Where appropriate, consider adding the action in addition to the destination, e.g. "[View more about the ACF Tech Data Surge Support Team](https://connect.acf.hhs.gov/acf-tech-data-surge-support-team)".


### Keep Documentation/README Files Updated

- Regularly review and update documentation and README to reflect changes in the project or software.
- Encourage contributions to documenation from the project team and community members.

## No-Code Project

### Scoping Documents

- Provide scoping documents that clearly define the boundaries of the project, detailing what will be included and what will not be included.

### Deliverables

- Include all required deliverables expected from the project, e.g., reports, excel files, graphs, etc,

### Project Briefs

- Provide a description of the project, including its purpose, goals and objectives. 
- List the specific output or deliverables expected from the project. 
- Outline the project timeline, including the key milestones and deadlines for completion.
- Define the roles and responsibilities of each team member involved in the project.
- Define the criteria for measuring the success of the project, e.g., satisfying client requirements, achieving target metrics.

### Technical Overviews

- Describe the tools, software and technologies that is utilized throught the project, e.g., project management tools, design software, communication platform and analytics tools, etc.
- Explain the approaches that is used to execute the project, e.g., A/B testing, sentiment analysis and thematic analysis.
- Outline infrastructure requirements used for the project, e.g., cloud infrastruture, hardware, equipment, etc.
- Discuss how data is collected, stored and analyzed throughout the project.
- Describe the processes that ensures the quality of project deliverables, e.g., peer review and user testing.

### Process Overviews

A document that describes the process overviews should include:

- **Initiation**: Define the project's objectives, scope, and initial requirements.
- **Planning**: Detail plan to determine the resources, timeline, and activities required to achieve project goals.
- **Execution**: Implement the plans that include coordinating team members, managing resources and completing project tasks.
- **Monitoring and Control**: Monitor the progress throughout the project lifecycle to ensure that the project is on track.
- **Communication**: Effectively communicate with stakeholders to keep them informed and engaged.
- **Quality Assurance**: Perform quality assurance to ensure that project deliverables meet the required standards and specifications.
- **Closure**: Finalize all project activities in the closure phase and deliver the final project outputs to the clients and document lessons learned for future reference.
- **Documentation**: Maintain the documentation to record project decisions, action taken and any relevant information.

### Lessons Learned

- Identify the challenges that arise during the project and outline the strategies for mitigating them.
- Record the mistakes that are made during the project and describe the potential strategies to avoid them in the future projects.

