# RHCSA Container Practice - Podman / RHEL9

This repository contains a **Dockerfile** designed for practicing a Red Hat RHCSA exam-style Podman/container question. It is intended for learning and hands-on practice.

## About

The Dockerfile creates a basic CentOS 7 container with the following setup:

- Creates directories `/incoming` and `/input`
- Sets the working directory to `/`
- Default command runs `/bin/bash`

This is useful for practicing container creation, volume mounts, and service management as required in RHCSA exam scenarios.

## RHCSA Exam Practice Scenario

Example question for practice:

> **Task:**  
> Create a container named `web` from an image `xyz` on `node1`.  
> - The service name should be `container-web`  
> - Configure it to start automatically across reboots  
> - Container should automount:
>   - `/local/outgoing` on the host → `/usr/local/out` in the container  
>   - `/local/input` on the host → `/usr/local/in` in the container  

This Dockerfile can be used as a base image or to simulate container behavior for such exercises.

## Usage

1. **Build the image**:
   ```bash
   podman build -t my-practice-image .
   Run the container:

podman run -it --name web -v /local/outgoing:/usr/local/out -v /local/input:/usr/local/in my-practice-image


Set up systemd service (for automatic start across reboots):

sudo podman generate systemd --name web --files --new
sudo mv container-web.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable container-web
sudo systemctl start container-web


Note: Adjust paths and container/image names according to your practice setup.

Requirements

RHEL 8/9 or CentOS 7/8

Podman installed

Basic knowledge of containers and systemd
