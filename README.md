# Private Docker Registry Project

## Overview
This project demonstrates how to set up a private Docker registry with authentication.

## What we did
- Installed Docker in WSL (Ubuntu)
- Created a private Docker registry
- Implemented authentication using htpasswd
- Pulled, tagged, pushed, and pulled Docker images

## Commands Used

### Run Registry
docker run -d -p 5000:5000 --name registry registry:2

### Login
docker login localhost:5000

### Push Image
docker push localhost:5000/my-nginx

### Pull Image
docker pull localhost:5000/my-nginx

### Verify
curl -u username:password http://localhost:5000/v2/_catalog
