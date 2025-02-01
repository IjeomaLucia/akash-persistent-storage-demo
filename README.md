# Akash Persistent Storage Demo

This project demonstrates the use of persistent storage on the Akash Network.  It uses a pre-built Busybox Docker image to showcase how persistent volumes work, without requiring any local Docker setup or complex application development.

## Introduction

Persistent storage is crucial for any application that needs to retain data across deployments, restarts, or updates.  This project provides a simple example of how to configure persistent storage on Akash using a deployment YAML file. While the deployed application itself is minimal (a Busybox container), the focus is on demonstrating and documenting the persistent volume configuration.

## Prerequisites

*   Akash CLI installed and configured.  See the official Akash documentation for installation instructions: [https://docs.akash.network/](https://docs.akash.network/)
*   A GitHub account.

## Project Setup

1.  Create a directory for your project (e.g., `akash-persistent-storage-demo`).
2.  Create a file named `deployment.yaml` inside this directory and paste the following content:

```yaml
version: "2.0"
services:
  fileserver:
    image: busybox:latest
    command: ["sh", "-c", "while true; do sleep 3600; done"]
    ports:
      - 80:80 # This port mapping is not used in this simplified example.
    volumes:
      - data:
          mountPath: /data
    persistentVolumes:
      data:
        size: "1Gi"
        class: default
