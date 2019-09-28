# Conda

Conda is what is called an environment manager. It means you can install new software without potentially breaking support for another part of the analysis.
We will be using conda to manage our python environment.

For quick reference I have bundled a 'cheat sheet' for conda, the original can be found here: https://conda.io/projects/conda/en/latest/user-guide/cheatsheet.html

I will keep this section brief for now as most things are easy enough to understand on the cheatsheet, and will update this page as/when questions are asked.

To install our python environment simply run:

    conda create --name py37 --file conda.txt
    
To activate the environment run:

    conda activate py37
    
To deactivate the environment run:

    conda deactivate

This will create the conda environment I use for bioinformatics, and I will update it as needed. For future reference for myself and others conda.txt was generated using:

    conda create --name <env> --file <this file>
