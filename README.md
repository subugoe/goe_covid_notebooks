# Göttingen Campus Covid Publications
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/subugoe/goe_covid_notebooks/HEAD)

## About
Author: Andreas Lüschow

Last updated: 2021/07/09


## Data used
We used the COVID-19 data set from Dimensions (https://www.dimensions.ai/covid19/). This data set is available via the [Google Cloud Platform](https://console.cloud.google.com/marketplace/product/digitalscience-public/covid-19-dataset-dimensions).


## Using this repository online

### Run Jupyter notebooks on Binder
Click here to run an online Binder environment: [Start Binder environment](https://mybinder.org/v2/gh/subugoe/goe_covid_notebooks/HEAD).

Binder automatically builds an environment with all necessary dependencies from this repository. You can then access the Jupyter notebooks inside the `./jupyter/` folder.

#### `./jupyter/data/`
These notebooks are used to load, query, transform and create SQL tables from [Google's BigQuery Platform](https://cloud.google.com/bigquery/).

To access BigQuery, you need to create your own project on Google Cloud Platform and get your private credentials to connect to this project from within the notebooks.

However, most of the tables needed for data analysis were already created by us and saved as `.csv` files under `./output/tables/`. These tables can be loaded from within a Jupyter notebook without the need to connect to BigQuery.

If you want to create custom tables that are not available  in `./output/tables/`, though,  you need to create your own BigQuery project with Dimensions COVID-19 data and connect it to the notebooks in `./jupyter/data/`. See "Using this repository locally" below.


#### `./jupyter/analysis/`
If you're interested in using the pre-compiled tables, you can find some example analyses inside the notebooks in this folder. They can be executed using [Binder](https://mybinder.org/v2/gh/subugoe/goe_covid_notebooks/HEAD). Here, no connection to  Google BigQuery is necessary.

The Jupyter notebook `dashboard.ipynb` illustrates how a simple dashboard can be created using the Göttingen Campus COVID-19 publication data. This notebook does only work locally, not on Binder.


More documentation can be found inside the notebooks themselves.

## Using this repository locally

### Clone the repository
`git clone https://github.com/subugoe/goe_covid_notebooks.git`

### Install dependencies
[Poetry](https://python-poetry.org/) is used for packaging and dependency management.
* Install [Poetry](https://python-poetry.org/)
* Run `poetry install` inside the root folder. This will install all necessary dependencies.

If you want to export poetry's dependencies to a `requirements.txt` file, call `poetry export --without-hashes -f requirements.txt --output requirements.txt `. 
(A `requirements.txt` file is needed if you want to support building a [Binder](https://jupyter.org/binder) environment from the repository.)

### Jupyter Notebook
Use `poetry run jupyter notebook` inside the root folder to run a local notebook server.

### BigQuery credentials and project name
Put a `bigquery_credentials.json` file outside the root folder of this repository (or change the path in the Jupyter notebook so that it points to your file) if you want to connect to a project on Google BigQuery from your local machine.

Same applies to a file `bigquery_project_name.txt` that contains the name of your BigQuery project database (e.g., "my-first-project.database").
