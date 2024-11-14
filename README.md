# Self-Hosted GitHub Actions Runner Lab

This repository contains scripts and configurations to set up a self-hosted GitHub Actions runner using Docker, specifically on Alpine Linux. The setup includes creating a repository, pushing initial contents, configuring a Docker image for the runner, and managing repository secrets.

## Prerequisites

- A GitHub account with a Personal Access Token (PAT) that has the following scopes:
  - `repo` (to access and create repositories)
  - `workflow` (to manage workflows)
  - `admin:repo_hook`
  - `read:packages`
- Docker installed on your machine.


### Directory Descriptions

- **lab/**: Contains files related to the lab setup.
- **lab_setup.sh**: The main script to create the repository, push contents, and set up the self-hosted runner.
- **runner/**: Contains the Dockerfile and the startup script for the self-hosted runner.
- **set_secret.sh**: A script to set GitHub secrets for the repository.

## Setup Instructions

1. **Clone the Repository:**
   Clone this repository to your local machine.

2. **Set Environment Variables:**
  Set the following environment variables in your terminal session:
  export LAB_PAT=<your-github-personal-access-token>

3. **Run the Setup Script as root:**
  Execute the setup script to create the repository and configure the self-hosted runner.

4. **Setting Secrets (Optional):**
  You can also set secrets for the repository. The `set_secret.sh` script will be invoked automatically by `lab_setup.sh`. You can modify the script to include specific secrets you want to add. 

## How It Works

- The `lab_setup.sh` script performs the following tasks:
- Creates a new GitHub repository if it does not exist.
- Pushes the contents of the `lab` directory to the repository.
- Retrieves a runner registration token.
- Builds a Docker image for the self-hosted runner from the `runner` directory.
- Runs the Docker container for the GitHub Actions runner.
- Configures the repository settings for GitHub Actions.

- The `start.sh` script is responsible for configuring the runner and starting it within the Docker container.

## Notes

- Ensure that Docker is running on your machine before executing the setup script.
- The Docker image and the runner configuration can be modified based on your specific requirements.
