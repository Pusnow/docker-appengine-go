# docker-appengine-go

Docker Image for the [Google App Engine Go environment](https://cloud.google.com/appengine/docs/go/) Go.

## Installation

```sh
docker pull gcr.io/gcpug-container/appengine-go
```

## Tags

All images installed `go` runtime, `gcloud` SDK and following components with `gcloud` way.

## Go 1.13

- Version: 1.13.7
- Base Image: [google/cloud-sdk](https://hub.docker.com/r/google/cloud-sdk/)

- [`latest`](1.13/debian/Dockerfile), [`1.13`](1.13/debian/Dockerfile)
  - Components
    - appengine-go
    - beta
    - cloud-datastore-emulator
    - emulator-reverse-proxy
    - pubsub-emulator
- [`slim`](1.13/slim/Dockerfile), [`1.13-slim`](1.13/slim/Dockerfile)
  - Components
    - appengine-go
    - beta
- [`alpine`](1.13/alpine/Dockerfile), [`1.13-alpine`](1.13/alpine/Dockerfile)
  - Components
    - appengine-go
    - beta

## Go 1.11

- Version: 1.11.13
- Base Image: [google/cloud-sdk](https://hub.docker.com/r/google/cloud-sdk/)

- [`1.11`](1.11/debian/Dockerfile)
  - Components
    - appengine-go
    - beta
    - cloud-datastore-emulator
    - emulator-reverse-proxy
    - pubsub-emulator
- [`1.11-slim`](1.11/slim/Dockerfile)
  - Components
    - appengine-go
    - beta
- [`1.11-alpine`](1.11/alpine/Dockerfile)
  - Components
    - appengine-go
    - beta

## Usage

To use this image, pull from [Container Registry](https://gcr.io/gcpug-container/appengine-go). See [Installation](#installation) section.

Verify the `go`, `gcloud` and `dev_appserver.py` commands:

```console
$ docker run --rm -it gcr.io/gcpug-container/appengine-go:latest gcloud version
Google Cloud SDK 220.0.0
alpha 2018.10.08
app-engine-go
app-engine-java 1.9.66
app-engine-python 1.9.77
app-engine-python-extras 1.9.77
beta 2018.10.08
bigtable
bq 2.0.34
cbt
cloud-datastore-emulator 2.0.2
core 2018.10.08
datalab 20180823
gsutil 4.34
kubectl 2018.10.08
pubsub-emulator 2018.10.08

$ docker run --rm -it gcr.io/gcpug-container/appengine-go:latest go version
go version go1.13.1 linux/amd64

$ docker run --rm -it gcr.io/gcpug-container/appengine-go:latest which dev_appserver.py
/usr/bin/dev_appserver.py
```

### Use on Circle CI 2.0

Create `.circleci/config.yml` to your repository.

```yaml
version: 2
jobs:
  build:
    working_directory: /go/src/github.com/YOUR/REPO
    docker:
      - image: gcr.io/gcpug-container/appengine-go
    steps:
      - checkout
      - run:
          command: YOUR_TEST_COMMAND
```

If you want to test the CI works, Install Circle CI 2.0 Command Line Interface:

https://circleci.com/docs/2.0/local-jobs/

Verify on local (required Docker environment on host OS):

```sh
cd /path/to/your_repository
circleci local execute --job JOB_NAME
```

## Committers

 * Kensuke Sano ([@sonatard](https://github.com/sonatard))

