Vivarium MSLT
=============================================

Research repository for updated Vivarium MSLT.

Installation
------------

To set up a new research environment, open up a terminal and run::

    $> conda create --name=vivarium_mslt python=3.11
    $> conda activate vivarium_mslt
    (vivarium_mslt) $> git clone https://github.com/population-interventions/vivarium_mslt_update
    (vivarium_mslt) $> cd vivarium_mslt_update
    (vivarium_mslt) $> pip install -e .


Make the data artifacts
------------
From the vivarium_mslt_update folder, run::

    (vivarium_mslt) $> make_artifacts minimal
    
Each scenario type has its own artifact. To change the scenario type, the files artifact.py, disease_modifier.py, epidemic.py must be changed. 
To specify the number of draws in the artifact (for multiple draw runs), the files disease_modifier.py, disease.py, epidemic.py, population.py must be changed.
(These processes have been improved in subsequent vivarium projects).


Make the model specification files
------------
From the vivarium_mslt_update folder, run::

    (vivarium_mslt) $> make_model_specifications
    
The model specification files (with suffix .yaml) will be containted in vivarium_mslt_update/model_specs.


Run a single simulation
------------
From the vivarium_mslt_update folder, run::

    (vivarium_mslt) $> simulate run -v model_specs/<model_spec>

To test
    (vivarium_mslt) $> simulate run -v model_specs/mslt_test.yaml

where *model_spec* is a valid .yaml model specification file.
Results are stored in vivarium_mslt_update/results


Run multiple simulations and multiple draws (untested)
------------
From the vivarium_mslt_update folder, run::

    (vivarium_mslt) $> run_uncertainty_analysis -d draw_num -s process_num model_specifications/model_spec1 model_specifications/model_spec2
    
where *draw_num* is the number of draws (not including draw 0) and *thread_num* is the number of processors to use (does not work on Windows if process_num > 1). An arbirtrary number of model_spec files can be used here.


Package versions (via pip freeze)
------------
aiocontextvars==0.2.2
certifi==2020.12.5
click==7.1.2
colorama==0.4.4
contextvars==2.4
decorator==4.4.2
immutables==0.15
Jinja2==2.11.3
loguru==0.5.3
MarkupSafe==1.1.1
networkx==2.5
numexpr==2.7.2
numpy==1.19.5
pandas==1.1.5
python-dateutil==2.8.1
pytz==2021.1
PyYAML==5.4.1
scipy==1.5.4
six==1.15.0
tables==3.6.1
# Editable install with no version control (tobacco==1.0.0)
-e c:\dev\repos\updatedvivarium\src
vivarium==0.10.1
win32-setctime==1.0.3
wincertstore==0.2
