Sai Phanindra Peddi project summary
I have a project which consist of 3 micro services written in different programming languages.   
1) A frontend services written in JavaScript
2) A backend service written in java
3) A message processing service in python.

Frontend service is to run on the customer browser. It provides URL of the backend service, so  the browser knows how to connect to backend. The backend service then connects with the  Message processing service for some internal message processing.
Every project contains Dockerfile which can be used for building docker images.

KUBERNETES	:
	Create one Kubernetes cluster with 2 environments - Development and Production.
	Every developer should have permission to deploy development environment just by running “kubectl apply” command from their laptop.
	Jenkins server must have permissions to deploy both development and production  environments.
	Jenkins must have permissions to connect to Kubernetes by running kubectl command.  Kubernetes will use credentials of deploy user (stored as a secret) when it wants to pull   images from harbor registry.
	Kubernetes cluster should run in a cloud environment – GCP, Azure or AWS
  
  JENKINS	
	Create a Jenkins Server and configure CI/CD job for development and production  environments. As soon a developer made a push to development branch, Jenkins will build and push docker image to harbor, then another job gets triggered in Jenkins which will deploy  development environment.
	Jenkins will run some testing – unit testing, or API testing as part of the development CI  Job.
	If all development activities – build, test, deploy, other tests are completed successfully,  it will trigger the production Job
	Production Job in Jenkins will merge the code from development branch to master and  deploy production environment.
	Jenkins uses "Jenkins" harbor user when it wants to push the code into registry.
