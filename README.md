# DevOpsProject

## Purpose of document

The purpose of this file is to serve as a documentation for DevOpsProject - Course work for FMI, year3. Made for the Modern DevOps Practices.

## Format of document

The format of this file, in order to explain what each job and step do in the DevOpsProject.yaml, is similar to this example:

	DevOpsProject.yaml:
	
		JOB1:
			- step1:
				- requirements(like repo secrets to be added to repo for app or account needed prior to step execution)
				- step summary	
			- step2:
				- requirements before step execution
				- step summary
		JOB2:
			-step1: ...
			-step2: ...
			....
		...

## DevOpsProject.yaml and what it does

DevOpsProject.yaml:
	
		Flake8:
			- step1: Checkout code
				- requirements before step execution : none
				- step summary: the first step for any job is to have completed the checkout code process, using the available git-hub action(available in the Git-Hub market place)
			- step2: Install flake8
				- requirements before step execution: none
				- step summary: install the flake8 app
      - step3: Check code with flake8
        - requirements before step execution: to have installed the flake8 app at a previous step in the current job
				- step summary: flake8 checks our Python codebase for errors, styling issues and complexity, given a filepath (such as the one in our workflow); flake8 check the 'app_test.py' in the 'src' directory file for the aforementioned issues. If the check finds issues, the step and job fail
    
		Editor-Conf-Check:
			-step1: ...
			-step2: ...
			....
		...
