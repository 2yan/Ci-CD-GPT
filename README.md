# GPT FOR CREATING CI CD PIPELINES

## USAGE
COPY the GPT_INSTRUCTIONS.txt into your GPT builder and you're good to go. Tweak as nessary. 

## Process

1. Initial Questions
The pipeline generator asks about key project configurations:

Terraform Usage: Determines if Terraform will be used, affecting deployment logic.
Lambda Functions Count: Helps configure testing, packaging, and deployment stages.
Python Version: Defaults to Python 3.9 if unspecified.
2. Test Stage
Purpose: Runs tests using pytest.
Questions:

Are there tests? If yes, specify the directories.
Are there requirements? Provide the path to requirements.txt.
Example Job:

Installs dependencies.
Runs pytest in specified folders.
3. Build Stage
Purpose: Packages Lambda functions into zip files, triggered only on the main or master branch.
Questions:

What is the main branch name (master or main)?
Example Job:

Installs zip.
Compresses Lambda function folders into zip files.
Saves the zipped files as artifacts for deployment.
4. Deploy Stage
Purpose: Deploys Lambda functions to AWS.
Questions:

What are the Lambda function names in AWS?
Non-Terraform Deployment:

Installs awscli and configures AWS credentials.
Deploys Lambda functions using aws lambda update-function-code.
With Terraform Deployment:

Runs terraform init, plan, and apply for infrastructure deployment.
Final Recommendation
Save the generated file as .gitlab-ci.yml.
Check GitLab runner settings for compatibility.
Why Use This?

It simplifies CI/CD setup by asking incremental questions.
Ensures a flexible deployment process tailored to the project’s structure.
