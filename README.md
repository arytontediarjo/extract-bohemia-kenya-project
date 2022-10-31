# Bohemia Kenya Project Forms Extraction
@author: Aryton Tediarjo (atediarjo@gmail.com)

## About
This Github repository is used as a Docker microservice for extracting forms from the Bohemia Kenya ODK Project. This repo will use a Docker to enable user to reproduce the process from start to finish. 

## Contributing:

### Getting Started
[Install Docker Desktop on Local Computer](https://docs.docker.com/desktop/)

### Build Docker Image
Use this [Dockerfile Reference](https://docs.docker.com/build/building/packaging/) to get familiar with Dockerfile. Once Dockerfile is built, run this command:

```zsh
docker build -t your_image_name .
```

### Testing Docker Image Locally
Before pushing to Dockerhub, create a local Docker container to test on your local computer.

```zsh
docker run extract-bohemia-kenya-project
```

On certain cases, you need to test pass environment variables for AWS and ODK authentication:

```zsh
docker run \
-e AWS_ACCESS_KEY=... \ 
-e AWS_SECRET_ACCESS_KEY=... \
-e AWS_SESSION_TOKEN=... \
-e AWS_REGION= 'us-east-1' \
-e ODK_CREDENTIALS_SECRETS_NAME='prod/odk-credentials' \
extract-bohemia-kenya-project
```

## Pushing to Dockerhub

To push to Dockerhub, you will only need to push your code to Github remote main branch, where Github Actions will do the CI/CD process for you.

```zsh
git push
```

You can find your dockerhub under databrew/<image_name>


