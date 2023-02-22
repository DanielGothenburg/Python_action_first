# Python_action_first
As per the example in Github documentation for running a Python based github action.

You find the workflow definition in folder .github/workflows. This is a required path in order for Github to recognize a file as a workflow definition.

In a file called: python-package.yml

This workflow definition so far only makes use of default capabilities which come with deploying to a Github hosted runner. So it uses that it has a python environment installed on the runner which enables using commands like pip.
'
By using pip command, it will directly download and isntall additional python packages. This is done in command:
 python -m pip install flake8 pytest
 

An alternative (or maybe combination?) would be to reference a requirements.txt file. If this approach is used then requirements.txt should exist in root of the repo.

When you run this action it will say it fails,however it is a warning.
Since in this workflow you make use of a standard workflow called setup-python@v3. This workflow seems to contain a deprecated command: `set-output` 

Hence when you run it under "Actions" menu, the steop where it runs setup-python@v3 will give below warning. And in a later step it will indicate it failed (but actually it is a warning)

Run actions/setup-python@v3
Warning: The `set-output` command is deprecated and will be disabled soon. Please upgrade to using Environment Files. For more information see: https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/
