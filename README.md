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
				- step summary: installs the flake8 app
    
      - step3: Check code with flake8
        - requirements before step execution: to have installed the flake8 app at a previous step in the current job
				- step summary: flake8 checks our Python codebase for errors, styling issues and complexity, given a filepath (such as the one in our workflow); flake8 check the 'app_test.py' in the 'src' directory file for the aforementioned issues. If the check finds issues, the step and job fail
    
		Editor-Conf-Check:
			- step1: Checkout code
				- requirements before step execution : none
				- step summary: checks-out the code
    
			- step2: Install Editor-Conf-Checker
			  - requirements before step execution : none
				- step summary: installs the Editor-Conf-Checker app
    
      - step3: Editor-Conf Check
        - requirements before step execution : have the Editor-Conf-Checker installed; have an exiting .editorconfig file in your reposity with preferred file configuration.
				- step summary: Checks the files in the repository according to the .editorconfig file. If the check finds issues, the step and job fail

    MarkdownFilesCheck:
  			- step1: Checkout code
  				- requirements before step execution : none
  				- step summary: checks-out the code
      
  			- step2: Markdown File Link Check
  			  - requirements before step execution : none
  				- step summary: Executes the 'ruzickap/action-my-markdown-link-checker@v1.1.2' available in the git-hub action marketplace; the check aims to see if any broken or invalid links are present, the step and job fail, giving a description of the links that are broken/invalid. If the check finds issues, the step and job fail

      UnitTest:
        - needs: for this job to begin the one(s) selected in the 'needs' row, they have to have finished successfully. 
        
  			- step1: Prepare repo
  				- requirements before step execution : none
  				- step summary: checks-out the code
      
  			- step2: Set up Python
  			  - requirements before step execution : none
  				- step summary: Sets up python using the 'actions/setup-python@v1' available in the GitHub Marketplace.

        - step3:  install requirements
				 - requirements before step execution : set-up python; have an existing requirements.txt with requirements for dependancies to install before next step
				 - step summary: uses python install dependencies using a filepath such as the one is our workflow (src/requirements.txt).
    
        - step4:  Test
				 - requirements before step execution : set-up python; installed dependancies;
				 - step summary: uses python to unittest a file throught its file path; in our example that file is app_test.py. If the test finds issues, the step and job fail
     
     GitLeaksCheck:
        - needs: for this job to begin the one(s) selected in the 'needs' row, they have to have finished successfully. 
        
  			- step1: Checkout code
  				- requirements before step execution : none
  				- step summary: checks-out the code
      
  			- step2: Gitleaks check
  			  - requirements before step execution : none
  				- step summary: uses the 'gitleaks/gitleaks-action@v2' action and the secret our GITHUB_TOKEN, which scans in order to find potential security vulnerabilities in our git repositories, files, and directories. If the check finds security leaks, the step and job fail.

     DB-Migration-Test:
         - needs: for this job to begin the one(s) selected in the 'needs' row, they have to have finished successfully. 
        
  			 - step1: 
  				 - requirements before step execution : none
           - services: sets up postgres service with image:postgres with env variables of the db(database), username and password, and with the options below
  				 - step summary: checks-out the code with git-hub action; executes the joshuaavalon/flyway-action@v3.0.0 to a given postgres db, which checks for any db migrations that have been added or been requested
      
    CodeCov:
         - needs: for this job to begin the one(s) selected in the 'needs' row, they have to have finished successfully. 
        
  			- step1: Checkout code
    				- requirements before step execution : none
    				- step summary: checks-out the code

        - step2: Set up Python
  			  - requirements before step execution : none
  				- step summary: Sets up python using the 'actions/setup-python@master' available in the GitHub Marketplace. Sets-up specifically python-version: 3.7 (could be another version, chosen by the writer of the workflow)

        - step3: Check code coverage
  			  - requirements before step execution : have python set-up from previous step in the current job; have added the CODECOV_TOKEN secret in the repositories secrets (Repo->Settings->Secrets and Variables->Add secret); have an account in CodeCov website in order to generate the Codecov token)
  				- step summary: Uses to check for code coverage files using the 'codecov/codecov-action@v3' action; If any are found, they are checked, if none are found, step finishes. If any issues are found, the step and job fail

      
         
		...












