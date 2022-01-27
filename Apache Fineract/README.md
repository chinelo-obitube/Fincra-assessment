# Set up Gitlab CI pipeline for Apache/Fineract repostory

## Steps
1. Fork the https://github.com/apache/fineract repository.
2. Create a new project: select the Run CI/CD for externatl repository option.
3. Choose the connect repository from github.
4. Select the forked repository and connect.
5. Go to the settings of the repository, go to the variables section, expand.
at this stage, we have to add our variables because we are running the CI pipeline on an AWS instance.
First variable: DEPLOY_SERVER_IP: <your instance public ip address>
Second variable: SSH_PRIVATE_KEY:<the private key of your instance>
6. Create the .gitlab-ci.yml file.
7. Commit and the pipeline starts automatically.

Any changes made to the files will automatically trigger a build.

