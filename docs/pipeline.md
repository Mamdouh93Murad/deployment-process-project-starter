# Pipeline Description

This is where we explain how the CI/CD Process takes place and how the pipeline works.
For this project, we are using CircleCI.
To Start this process:
1. Link your Github Account to Your CircleCI account
1. Set up the Project in CircleCI and Specify where to Find the circleci config.yaml file
1. Edit The config.yaml file to add proper steps

## How our CI/CD Works in this Project:
The config.yaml file in this project states the steps taken in order to install, build and deploy our project. 

1. it runs the orbs, which is the fundemental step to install required software and frameworks, such as node, aws cli, eb. 
1. we specify next each job, a job is what we tell the program to execute, usually it installs, builds or deploys dependencies and project. 

    ### Jobs:
    here the program runs jobs which are written in the root level package.json file
    1. `npm run frontend:install` which installs all the dependencies required to run the frontend application.
    1. `npm run api:install` which installs all the dependencies required to run the backend application.
    1. `npm run frontend:lint` which runs the lint library to fix code errors in the frontend application/code.
    1. `npm run frontend:build` which builds the frontend application.
    1. `npm run api:build` which builds the backend application.
    1. `npm run deploy` which runs the deployment process; where the frontend and backend applications are deployed and AWS services required are configured/created.