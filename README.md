# Dockerfile Bug: Inconsistent Base Image

This repository demonstrates a common error in Dockerfiles: using an unstable base image (`ubuntu:latest`). This can lead to build inconsistencies across different environments.

The `Dockerfile` uses `ubuntu:latest`, which pulls the very latest version of Ubuntu, which may not always be what's desired.  This can cause unexpected build failures or runtime errors if dependencies or system libraries change between builds.

The `Dockerfile_fixed` provides a solution by specifying a precise version of Ubuntu, ensuring consistent builds and better reproducibility.

## How to Reproduce

1. Clone this repository.
2. Build the original Dockerfile: `docker build -t unstable-image -f Dockerfile .`
3. Build the fixed Dockerfile: `docker build -t stable-image -f Dockerfile_fixed .`
4. Compare the image sizes and examine their contents to see the difference.

## Solution

The problem is solved by specifying a fixed tag of Ubuntu, such as `ubuntu:22.04`.  This ensures that the build will use the same Ubuntu version consistently, resolving the reproducibility issue.