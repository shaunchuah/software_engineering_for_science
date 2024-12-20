# Docker and Containerization

<iframe style="width:100%; aspect-ratio:16/9;" src="https://www.youtube.com/embed/Gjnup-PuquQ?si=X3YHnVs7rP7ixKZz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Containerization is a lightweight form of virtualization that allows you to package applications and their dependencies into containers. You can specify the entire stack of dependencies from the operating system, installed os packages through to python packages and your application code. These containers can then run consistently across various computing environments - the same containers can run whether it is on linux, windows, MacOS etc. Unlike traditional virtual machines, containers share the host system's kernel, making them more efficient and faster to start. These containers can then be deployed to the cloud and scaled up or down easily.

## What is Docker?

Docker is a platform that automates the building, management, and deployment of containerized applications. Docker is the most common tool used for containerization due to its ease of use and widespread adoption. There are other alternatives if required, such as Podman.

## Key Concepts

- **Docker Engine**: The core part of Docker, it allows you to build and run containers. It consists of a Docker daemon that runs on the host machine and a Docker CLI (command-line interface) for interacting with the Docker daemon.

- **Docker Images**: Immutable snapshots of your application and its environment. These images are built from a Dockerfile and contain everything needed to run the application, including the code, runtime, libraries, and configurations.

- **Docker Containers**: Running instances of Docker images. Containers are isolated from each other and the host system, but can interact through defined channels.

- **Dockerfile**: A text file that contains instructions for building a Docker image. It specifies the base image, the application's code, dependencies, and configuration.

- **Docker Hub**: A cloud-based repository where you can find and share Docker images. You can pull images from Docker Hub or push your own images to it. AWS and Azure also have their own container registries where you can store images of your applications.

## Getting Started with Docker

### Step 1: Install Docker

Docker can be installed on various operating systems, including Windows, macOS, and Linux. Follow the instructions on the official [Docker website](https://www.docker.com/) to install Docker on your machine.

### Step 2: Write a Dockerfile

Create a file named Dockerfile in your project directory. Here’s an example for a simple Python application:

```dockerfile title="Dockerfile"
# Use an official Python runtime as a parent image
FROM python:3.12-slim

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

### Step 3: Build the Docker Image

Use the Docker CLI to build the image from the Dockerfile:

```sh
docker build -t my-python-app .
```

### Step 4: Run a Docker Container

Run the container from the image you just built:

```sh
docker run -p 4000:80 my-python-app
```

This command maps port 80 in the container to port 4000 on your local machine.

### Step 5: Access Your Application

Open your web browser and go to <http://localhost:4000>. You should see your application running.

## Applying Docker to Bioinformatics Packages

Here are some examples of how I used Docker to containerize bioinformatics applications: <https://github.com/shaunchuah/docker_builds>

### Example container with Kraken and Bracken installed

Here is an example of packaging Kraken and Bracken into a single container to increase the efficiency of my NextFlow pipeline by reducing the amount of data transferred between the computing cluster and cloud object storage.

```dockerfile title="Dockerfile"
# CONTAINER 
# shaunchuah/kraken_bracken
#
# SPECIAL NOTES
# For kraken2 and bracken, usage is as per original manual.
# For KrakenTools, usage is similar to the manual except for the path.
# Use 'python /krakentools/<script_name> <arguments>' instead.
FROM python:3.10-buster

# Upgrade by changing version numbers here
ARG K2VER="2.1.2"
ARG BRACKEN_VERSION="2.6.2"
ARG KRAKENTOOLS_VERSION="1.2"

# install dependencies and cleanup apt garbage
RUN apt-get update && apt-get -y --no-install-recommends install \
    wget \
    ca-certificates \
    zlib1g-dev \
    make \
    g++ \
    rsync \
    build-essential \
    cpanminus && \
    rm -rf /var/lib/apt/lists/* && apt-get autoclean

# perl module required for kraken2-build
RUN cpanm Getopt::Std

# DL Kraken2, unpack, and install
RUN wget https://github.com/DerrickWood/kraken2/archive/v${K2VER}.tar.gz && \
    tar -xzf v${K2VER}.tar.gz && \
    rm -rf v${K2VER}.tar.gz && \
    cd kraken2-${K2VER} && \
    ./install_kraken2.sh . && \
    mkdir /data /kraken2-db

ENV PATH="$PATH:/kraken2-${K2VER}" \
    LC_ALL=C

# DL Bracken
WORKDIR /bracken

RUN wget https://github.com/jenniferlu717/Bracken/archive/v${BRACKEN_VERSION}.tar.gz && \
    tar -xzf v${BRACKEN_VERSION}.tar.gz && \
    rm -rf v${BRACKEN_VERSION}.tar.gz && \
    cd Bracken-${BRACKEN_VERSION} && \
    chmod +x ./install_bracken.sh && \
    ./install_bracken.sh

ENV PATH="/bracken/Bracken-${BRACKEN_VERSION}:${PATH}"

# Install krakentools
WORKDIR /krakentools
RUN wget https://github.com/jenniferlu717/KrakenTools/archive/v${KRAKENTOOLS_VERSION}.tar.gz && \
    tar -xzf v${KRAKENTOOLS_VERSION}.tar.gz && \
    rm -rf v${KRAKENTOOLS_VERSION}.tar.gz && \
    mv KrakenTools-${KRAKENTOOLS_VERSION}/* .

ENV PATH="/krakentools:${PATH}"

WORKDIR /data
CMD ["bash"]
```

## VSCode Dev Containers

Full documentation here: <https://code.visualstudio.com/docs/devcontainers/containers>

Visual Studio Code (VSCode) has a feature called Dev Containers that allows you to develop inside a container. This is useful for ensuring that your development environment is consistent across different machines and for sharing your development environment with others. You can define your development environment in a `devcontainer.json` file, which specifies the Dockerfile to use, the extensions to install, and other settings.

Example Project Structure:

```bash
my_project/
├── .devcontainer/
│   └── devcontainer.json
├── requirements.txt
└── Dockerfile
```

An example Python dev container configuration:

```json title=".devcontainer/devcontainer.json"
{
    "name": "[Optional] Your project name here",
    // You can also use docker compose for more complex setups
    // "dockerComposeFile": "../docker-compose.yml",
    "build": {
        "dockerfile": "Dockerfile",
        "context": ".." // Dockerfile in the root of the project
    },
    "extensions": [
        "ms-python.python"
    ]
}
```

The corresponding requirements.txt file:

```plaintext title="requirements.txt"
numpy==2.2.0
pandas==2.2.3
matplotlib==3.9.4
scikit-learn==1.6.0
```

and the corresponding Dockerfile in the root of your project:

```dockerfile title="Dockerfile"
FROM python:3.12-slim

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt 

# Set the default shell to bash
CMD ["/bin/bash"]
```

With this setup, you can open your project in VSCode and select "Reopen in Container" to start developing inside the container. You can also easily upgrade versions by changing the corresponding files and rebuilding the container.

!!! info
    This is an alternative way to manage python environments and dependencies. It also means you can upgrade python versions easily.

## Trusted Research Environments

Trusted research environments are currently the way to access unconsented clinical data via SafeHaven or DataLoch. Many TREs essentially use containers to provision a workspace within a secure network from which you get access to the data. Understanding SSH, Docker, and containerization is essential for working within these TREs.
