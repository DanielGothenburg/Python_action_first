# Python_action_first
As per the example in Github documentation for running a Python based github action.

You find the workflow definition in folder .github/workflows. This is a required path in order for Github to recognize a file as a workflow definition.

In a file called: python-package.yml

This workflow definition so far only makes use of default capabilities which come with deploying to a Github hosted runner. So it uses that it has a python environment installed on the runner which enables using commands like pip.

The workflow will:

Take any files in root directory and try and run these files. Currently this covers:

app.py -> A python application which prints "Hellow World" and activates (import) a library

requirements.text -> a file which is used by Python to find out if there are libraries to be installed (such as the library used by program app.py)

There are also other ways to import libraries, as is shown in the action definition. Details follow here:

By using pip command, it will directly download and isntall additional python packages. This is done in command:
 python -m pip install flake8 pytest
 You can of course install more packages in this way using pip as part of the workflow definition file (in this ex file python-package.yml)
 

An alternative (or maybe combination?) would be to reference a requirements.txt file. If this approach is used then requirements.txt should exist in root of the repo. See more below

When you run this action it will say it fails,however it is a warning.
Since in this workflow you make use of a standard workflow called setup-python@v3. This workflow seems to contain a deprecated command: `set-output` 

Hence when you run it under "Actions" menu, the steop where it runs setup-python@v3 will give below warning. And in a later step it will indicate it failed (but actually it is a warning)

Extract from the instruction page reg this warning triggered by this action:

Run actions/setup-python@v3
Warning: The `set-output` command is deprecated and will be disabled soon. Please upgrade to using Environment Files. For more information see: https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/

In this action definition in the file python-package.yml it contains a condition for checking if requirements.txt exists. When I have added the requirements.txt to root of repo and in this file listed at least one package then it will install also this/these packages. 
You find that this step is completed if you navigate as folows underv the Actions tab: 

Go to the workflow which has run, here choose the job (in this case there are 3 jobs thanks to the matrix command). Once you have chosen one job, you can see the steps, go to the step "Install dependencies".

Here you find any python packages installed directly with pip install, but also any packages installed via file requirements.txt
