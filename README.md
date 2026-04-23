# 🚀 Private Docker Registry with Authentication (DevOps Project)

## 📌 Project Overview
This project demonstrates how to set up a **Private Docker Registry** using Docker and secure it with authentication. It allows users to store, manage, and retrieve Docker images locally instead of using public registries like Docker Hub.

This project represents a real-world **DevOps workflow**, focusing on containerization, image management, and secure storage.

---

## 🎯 Objectives
- Understand Docker workflow  
- Create a private Docker registry  
- Implement authentication using htpasswd  
- Push and pull Docker images  
- Verify stored images using API  

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
- **Tagging** → Naming an image for registry  

---

## 🏗️ Architecture
Docker Hub → Local System → Private Registry → Push/Pull Images  

---

## ▶️ How to Run the Project
1. Open Ubuntu (WSL) terminal  
2. Install Docker  
3. Start Docker service  
4. Execute commands step-by-step  
5. Ensure Docker is running  

---

## ⚙️ Implementation Steps

### 1. Install Docker
```bash
sudo apt update
sudo apt install docker.io -y
2. Start Docker Service
sudo service docker start
3. Run Docker Registry
docker run -d -p 5000:5000 --name registry registry:2
4. Setup Authentication
sudo apt install apache2-utils -y
mkdir auth
htpasswd -Bc auth/htpasswd anuja_shinde
5. Run Registry with Authentication
docker rm -f registry
docker run -d -p 5000:5000 --name registry \
-v $(pwd)/auth:/auth \
-e REGISTRY_AUTH=htpasswd \
-e REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd \
-e REGISTRY_AUTH_HTPASSWD_REALM="Registry Realm" \
registry:2
6. Pull Docker Image
docker pull ubuntu
7. Tag Image for Local Registry
docker tag ubuntu localhost:5000/my-ubuntu
8. Push Image to Private Registry
docker push localhost:5000/my-ubuntu
9. Pull Image from Private Registry
docker pull localhost:5000/my-ubuntu
10. Verify Stored Images
curl -u anuja_shinde:password http://localhost:5000/v2/_catalog
📸 Screenshots

(Add screenshots from the screenshots folder)

Docker container running (docker ps)
Login success (docker login)
Image push output
Image pull output
Registry verification output
📊 Output
Private Docker registry successfully created
Authentication implemented
Image (my-ubuntu) pushed and pulled successfully
Registry verified using API

Example Output:

{"repositories":["my-ubuntu"]}
🔐 Security Features
Authentication using username and password
Prevents unauthorized access
Ensures secure image storage
💡 Use Cases
Private Docker image storage
DevOps pipelines
Secure deployments
Internal organizational use
📈 Future Enhancements
Add HTTPS using SSL certificates
Deploy on cloud platforms
Integrate with CI/CD tools
Implement role-based access control
🎤 Conclusion

This project demonstrates a secure and efficient way to manage Docker images using a private registry, reflecting real-world DevOps practices.

👩‍💻 Author

Anuja Shinde
