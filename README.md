# Overview

Complete this with an overview of your project>

## Project Plan
Project Plan

* https://trello.com/b/QpMItK6Y/udacity-project-ii - Board Link
* A link to a spreadsheet that includes the original and final project plan>

## Instructions
 
* Architectural Diagram (Shows how key parts of the system work)>

Steps to run this project
Create a Github Repo (if not created)
Open Azure Cloud Shell
Create ssh-keys in Azure Cloud Shell
Upload ssh-keys to Github
Create scaffolding for project (if not created)
Makefile
Should look similar to the file below

install:
	pip install --upgrade pip &&\
		pip install -r requirements.txt

test:
	python -m pytest -vv test_hello.py


lint:
	pylint --disable=R,C hello.py

all: install lint test
requirements.txt
The requirements.txt should include:

pylint
pytest
Create a python virtual environment and source it if not created
python3 -m venv ~/.myrepo
source ~/.myrepo/bin/activate
Create initial hello.py and test_hello.py
hello.py

def toyou(x):
    return "hi %s" % x


def add(x):
    return x + 1


def subtract(x):
    return x - 1
test_hello.py

from hello import toyou, add, subtract


def setup_function(function):
    print("Running Setup: %s" % {function.__name__})
    function.x = 10


def teardown_function(function):
    print("Running Teardown: %s" % {function.__name__})
    del function.x


### Run to see failed test
#def test_hello_add():
#    assert add(test_hello_add.x) == 12

def test_hello_subtract():
    assert subtract(test_hello_subtract.x) == 9
Run make all which will install, lint and test code.

Setup Github Actions in pythonapp.yml

name: Python application test with Github Actions

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Python 3.5
      uses: actions/setup-python@v1
      with:
        python-version: 3.5
    - name: Install dependencies
      run: |
        make install
    - name: Lint with pylint
      run: |
        make lint
    - name: Test with pytest
      run: |
        make test
Commit changes and push to Github

Verify Github Actions Test Software

Run project in Azure Shell

Push container to Azure Registery

Setup Azure Pipelines

Setup Kubernetes Cluster

Deploy to Kubernetes

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
moussa@Azure:~/ML_Project_Azure-Devops$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application

> 

## Enhancements

1) There seem to be a typo on Makefile spacing, unless that was on purpose.
2) The instructions shows the Azure pipeline flow but the deployment center is soon to be removed.
3) Assist a bit more with the Azure Devops suite instead of just Pipeline.

## Demo 

<TODO: Add link Screencast on YouTube>


