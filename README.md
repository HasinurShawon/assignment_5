[![CICD Pipeline](https://github.com/HasinurShawon/assignment_5/actions/workflows/cicd.yml/badge.svg?branch=main)](https://github.com/HasinurShawon/assignment_5/actions/workflows/cicd.yml)

### Assignment 5

**_Functional Application Deployment:_**

The Node.js application was successfully deployed using a GitHub Actions CI/CD pipeline and a self-hosted runner.
* The deploy job runs only after the test job completes successfully
* The application is managed by PM2 and the service runs on port 3000.
* Nginx is configured as a reverse proxy to forward incoming HTTP requests from port 80 to the Node.js application.
This confirms that the application is fully functional and automatically deployed through the CI/CD pipeline.


**_Challenges Encountered and Solutions:_**

* PM2 Not Found on Self-Hosted Runner

Challenge:
The deployment job failed initially because PM2 was not available on the self-hosted runner, even though it was used in the GitHub Actions workflow.

Solution:
Node.js and PM2 were installed manually on the server as a one-time setup. This ensured that the CI/CD pipeline could manage the application process without reinstalling system dependencies on every run.

* 502 Bad Gateway Error from Nginx

Challenge:
After configuring Nginx, accessing the application returned a 502 Bad Gateway error.

Solution:
The issue was identified as the Node.js application not running and not listening on port 3000. After starting the application with PM2 and confirming the port was active, the Nginx reverse proxy worked correctly.
