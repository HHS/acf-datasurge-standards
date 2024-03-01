# Notebooks
## Purpose of Notebooks
"A notebook is an interactive document displayed in your browser which contains source code, e.g. Python and R, as well as rich text elements like paragraphs, equations, figures, links, etc. This combination makes it extremely useful for explorative tasks where the source code, documentation and even visualisations of your analysis are strongly intertwined." - Florian Wilhelm

Notebooks are a great way to present data analysis projects. They also are a useful tool in testing out code before turning it into a single script.
## How to Structure your Notebook
Notebooks will start with a code block that includes relevant package imports. It may also be helpful to include a markdown cell that outlines for the reader what is housed in the rest of the file or why the analysis was conducted.

Because notebooks can include a combination of markdown and code blocks, using markdown cells to identify new sections of a notebook is good practice. For example, you may have a section at the beginning of your notebook where you read in a dataset and do some initial analysis. This collection of code cells could start with a markdown cell with the title: "Exploratory Analysis". Once your analysis moves away from a solely exploratory direction, you can include a new markdown cell that identifies this new section of the notebook. This [Markdown Cheat Sheet](https://www.markdownguide.org/basic-syntax/) can be helpful in formatting useful, concise markdown cells (and files!).

Here are some example notebooks that follow a nice structure:
- [Sci-kit Learn Cookbook](https://github.com/ibm-et/jupyter-samples/blob/master/scikit-learn/sklearn_cookbook.ipynb)
- [Daily Temperature Analysis](https://github.com/ibm-et/jupyter-samples/blob/master/noaa/etl/noaa_hdta_etl.ipynb)
## Common Pitfalls
Because notebooks contain independent cells that can be run out of order, it is easy to overwrite variable names and confuse test code for final code. Because of this, it is important to abstract code into functions whenever possible to cut down on the possibility of reproducibility issues.

Once these functions have been finalized (and include great doc strings!) it is good practice to move them into a python module that can be imported with your other packages. This is especially important when you have a longer notebook that includes a lot of code.
## References
- [Florian Wilhelm - Working Efficiently with JupyterLab Notebooks](https://florianwilhelm.info/2018/11/working_efficiently_with_jupyter_lab/)
- [Jupyter Documentation](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/examples_index.html)
