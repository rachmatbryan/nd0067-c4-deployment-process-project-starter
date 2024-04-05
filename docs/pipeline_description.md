# Pipeline Description

This document details the Continuous Integration and Continuous Deployment (CI/CD) pipeline configured in CircleCI for the udagram application. This pipeline ensures automated testing, building, and deployment of the application to AWS Elastic Beanstalk upon successful integration.

## Jobs

### build

This job is crucial for preparing the application for deployment by performing tasks like dependency installation and code compilation.

#### Steps

- **Spin up environment**: Initializes the Docker environment for the job using a pre-defined Node.js Docker image.
- **Preparing environment variables**: Configures the required environment variables for the build process.
- **Install Node.js 14.15**: Ensures the specific version of Node.js required by the application is installed.
- **Install Front-End Dependencies**: Installs all the dependencies needed for the frontend application as specified in `package.json`.
- **Install API Dependencies**: Installs the necessary dependencies for the API/backend portion of the application.
- **Front-End Lint**: Performs linting on the frontend code to ensure it adheres to set coding standards.
- **Front-End Build**: Compiles the frontend source code into a distributable format.
- **API Build**: Processes the backend source code into a ready-to-run state for the production environment.

### deploy

This job takes care of deploying the built application to AWS Elastic Beanstalk, which involves setting up AWS credentials and using the AWS and Elastic Beanstalk CLI.

#### Steps

- **Install Node.js 14.15**: Installs Node.js which is required for running the deployment scripts.
- **Setting Up Elastic Beanstalk CLI**: Installs and configures the Elastic Beanstalk Command Line Interface, necessary for deploying the application to the EB environment.
- **Install AWS CLI - latest**: Installs the latest version of the AWS CLI, providing a way to manage AWS services directly from the terminal.
- **Configure AWS Access Key ID**: Sets up the AWS credentials, allowing CircleCI to authenticate with AWS and carry out deployment tasks.
- **Checkout code**: Obtains the most recent code commit from the version control system for deployment.
- **Deploy App**: Executes the deployment commands that may include transferring the built application to S3, updating an Elastic Beanstalk environment, or other deployment steps as defined in the project's deployment scripts.

## Workflows

The workflow defines the order and conditions for job execution.

- **build**: Executes the `build` job.
- **hold**: A manual gate requiring approval before proceeding to deployment. This ensures that deployment happens only after deliberate confirmation.
- **deploy**: Upon approval in the `hold` step, this job automates the deployment of the application to the specified AWS Elastic Beanstalk environment.

## Notes

- Each step within the `build` and `deploy` jobs might correspond to specific scripts defined within the project's `package.json`. Ensure these scripts are appropriately defined to carry out the necessary build and deployment actions.
- The `deploy` job, in particular, should be configured to handle the specifics of pushing the application to AWS Elastic Beanstalk, which may include packaging the application files, handling versioning, and updating the environment.
