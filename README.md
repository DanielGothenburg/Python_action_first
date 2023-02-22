# Python_action_first
As per the example in Github documentation for running a Python based github action.

You find the workflow definition in folder .github/workflows. This is a required path in order for Github to recognize a file as a workflow definition.

In a file called: python-package.yml

This workflow definition so far only makes use of default capabilities which come with deploying to a Github hosted runner. So it uses that it has a python environment installed on the runner which enables using commands like pip.
'
By using pip command, it will directly download and isntall additional python packages. This is done in command:
 python -m pip install flake8 pytest
 

An alternative (or maybe combination?) would be to reference a requirements.txt file. If this approach is used then requirements.txt should exist in root of the repo.
