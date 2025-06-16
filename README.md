**Tech Stack**
<p align="left"> 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" title="Python" alt="Python" width="40" height="40"/>&nbsp; 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" title="VS Code" alt="VS Code" width="40" height="40"/>&nbsp; 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flask/flask-original.svg" title="Flask" alt="Flask" width="40" height="40"/>&nbsp; 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" title="Docker" alt="Docker" width="40" height="40"/>&nbsp; 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-plain.svg" title="Kubernetes" alt="Kubernetes" width="40" height="40"/>&nbsp; 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/googlecloud/googlecloud-original.svg" title="GKE" alt="Google Cloud / GKE" width="40" height="40"/>&nbsp; 
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/github/github-original.svg" title="GitHub Actions" alt="GitHub" width="40" height="40"/>&nbsp; </p>
Highlights

1.	CI-CD using GIthub Actions.
2.	Project on pc – push to github repo- now ci-cd start – GCP setup - checkout code from github repo-dockerising the project (building image)-push the image to GCR-stored in artifacts repo-take this image and deploy to GKE.

Step 1
Project setup
1.	Creating virtual Environment in project folder.
2.	Creating required folders and files. (artifacts for outputs, pipeline folder, src where main project code lies, (static , templates for html,css,js and flask automatically finds them in project directory), utils for common functions, requirements and setup file. To make a folder a package we need to create a __init__.py file inside it so that the methods/files can be accessed from other places.
3.	Next, we code for setup, custom exceptions, logger, requirements files (basic things at first like numpy, pandas) .
4.	Then we run setup.py in venv in cmd using pip install -e . This will install all the required dependencies for the project make the project directory ready for next steps. This step automatically created a folder with project name given in the setup.py

Step 2
1.	After jupyter notebook testing we start with Data processing.
2.	Create data_processing.py, code it and test. You should see the artifacts in the project directory.
3.	Now model_training.py in src, code it and test. Should see the model.pkl in the artifacts.

Step 3
User App building using Flask
1.	Create application.py in root , code and test. Make sure flask in requirements.
2.	Create index.html, style.css and code, Run.

Step 4
Training Pipeline, Data and Code versioning
1.	Create training_pipeline.py in pipeline folder, code and run.

Step 5
GCP setup
1.	Go to Gcp and enable some API’s required for the project. 
2.	Kubernetes Engine API, google container registry API, compute Engine API, IAM API, cloud build API, Cloud storage API.
3.	Search for artifact registry. Create repo- select docker-region uscentral lowa-create.
4.	Next create a service account in IAM- name of account- permissions (owner, storage object viewer, storage object admin, artifact registry administrator, artifact registry writer)-Done.
5.	Create key for service account- hamburger- manage keys- add key- json-create.
6.	Now we need to create cluster. So go to kubernetes engine-cluster- create- give name- select region same as in GCR- tick for “access using DNS”-review-create.
7.	now copy the json file to project root in vscode-rename-add to gitignore.
8.	Now push the code to GIthub repo.
9.	Create Dockerfile in root, code it.
10.	Then create Kubernetes_deployment.yaml and code it.
11.	 Now go to github repo settings-secrets & variables-github actions-new repo secret-give name-copy the project id from gcp and paste-create.
12.	Add another secret key- give name- copy the json content and paste in secret.
13.	Now create in root .github-workflows-deploy.yml
14.	Install github actions extension in vscode. You should a git image beside the deploy.yml
15.	Now code the deploy.yml. And push the changes to github.
16.	As configured, now the github actions triggers the CI-CD, go to actions, there you the see steps being excuted. After the successful execution, go to registry you will the image and go to GKE and workloads- you will see the pods running and endpoint. Click on it and test.
17.	Done.
18.	Clean up Artifacts, clusters etc 

