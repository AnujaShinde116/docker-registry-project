# 🚀 Private Docker Registry with Authentication

## 📌 Project Overview
This project demonstrates how to set up a **Private Docker Registry** on a local system using Docker, with **authentication enabled** for secure image storage and access.

It simulates a real-world DevOps workflow where organizations store and manage their own Docker images instead of relying on public registries.

---

## 🎯 Objectives
- Understand Docker architecture and workflow  
- Create and configure a private Docker registry  
- Implement authentication using `htpasswd`  
- Push and pull Docker images securely  
- Verify stored images using registry APIs  

---

## 🛠️ Technologies Used
- Docker  
- Ubuntu (WSL)  
- Docker Registry  
- Apache htpasswd  

---

## 🧠 Key Concepts
- **Docker Image** → Packaged application with dependencies  
- **Docker Container** → Running instance of an image  
- **Docker Registry** → Storage for Docker images  
- **Tagging** → Naming images for registry storage  

---

## 🏗️ Architecture
Docker Hub → Pull Image → Local System → Private Registry → Push/Pull

---

## ⚙️ Implementation Steps

### 1. Install Docker
sudo apt update  
sudo apt install docker.io -y  

### 2. Start Docker Service
sudo service docker start  

### 3. Run Docker Registry
docker run -d -p 5000:5000 --name registry registry:2  

### 4. Setup Authentication
sudo apt install apache2-utils -y  
mkdir auth  
htpasswd -Bc auth/htpasswd username  

### 5. Run Registry with Authentication
docker run -d -p 5000:5000 --name registry \
-v $(pwd)/auth:/auth \
-e REGISTRY_AUTH=htpasswd \
-e REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd \
registry:2  

### 6. Pull Docker Image
docker pull nginx  

### 7. Tag Image for Local Registry
docker tag nginx localhost:5000/my-nginx  

### 8. Push Image to Private Registry
docker push localhost:5000/my-nginx  

### 9. Pull Image from Registry
docker pull localhost:5000/my-nginx  

### 10. Verify Stored Images
curl -u username:password http://localhost:5000/v2/_catalog  

---

## 📊 Output
- Private Docker registry successfully created  
- Authentication enabled using htpasswd  
- Docker image (nginx) pushed and retrieved successfully  
- Registry contents verified via API  

---

## 🔐 Security Features
- Authentication using username and password  
- Only authorized users can access the registry  
- Prevents unauthorized image usage  

---

## 💡 Use Cases
- Internal company Docker image storage  
- Secure DevOps pipelines  
- Offline/private deployments  
- Testing containerized applications  

---

## 📈 Future Enhancements
- Add HTTPS using SSL certificates  
- Deploy registry on cloud platforms  
- Integrate with CI/CD pipelines  
- Improve access control  

---

## 🎤 Conclusion
This project demonstrates the implementation of a secure private Docker registry, enabling efficient and controlled management of Docker images in a local environment.

---

## 👩‍💻 Author
Anuja Shinde
