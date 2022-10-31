# Bohemia Kenya Project Forms Extraction
@author: Aryton Tediarjo (atediarjo@gmail.com)
@reviewedBy: Joe Brew

## About
This Github repository is used as a Docker microservice for extracting forms from the Bohemia Kenya ODK Project. This repo will use a Docker to enable user to reproduce the process from start to finish. 

## Contributing

### Clone Repository
```zsh
git clone https://github.com/arytontediarjo/extract-bohemia-kenya-project.git
```

### Create a new branch
```zsh
git checkout -b feature_branch
git push origin feature_branch
```
### Reproduce Analysis Environment
This project uses [R renv](https://rstudio.github.io/renv/articles/renv.html) to act as a virtual environment and snapshots the library requirements and the version being used during the analysis. 

```zsh
# cd to your cloned project
cd ..relative_path/extract-bohemia-kenya-project
```
In the project directory, run these following R commands:

```r
install.packages("renv")
renv::init(bare=TRUE)
renv::restore()
```

Once sync-ed with the project environment, you can start running the R scripts. All R-packages are being indexed into a Lockfile (renv.lock). To add more packages you can do the usual R installation and snapshot that information into the Lockfile.

```r
install.packages('your_new_package')
renv::snapshot()
```

## Getting Started with Docker
[Install Docker Desktop on Local Computer](https://docs.docker.com/desktop/)

### Build Docker Image
Use this [Dockerfile Reference](https://docs.docker.com/build/building/packaging/) to get familiar with Dockerfile. Once Dockerfile is built, run this command:

```zsh
docker build -t extract-bohemia-kenya-project .
```

### Testing Docker Image Locally
Before pushing to Dockerhub, test it locally:

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

You can find your Docker Image in Dockerhub under the name **databrew/extract-bohemia-kenya-project**


