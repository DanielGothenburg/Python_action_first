# Python_action_first
As per the example in Github documentation for running a Python based github action.

You find the workflow definition in folder .github/workflows. This is a required path in order for Github to recognize a file as a workflow definition.

In a file called: python-package.yml

This workflow definition so far only makes use of default capabilities which come with deploying to a Github hosted runner. So it uses that it has a python environment installed on the runner which enables using commands like pip.
