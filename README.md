# 🚀 Private Docker Registry with Authentication (DevOps Project)

## 📌 Project Overview
This project demonstrates the implementation of a **Private Docker Registry** using Docker with authentication enabled. It allows users to securely store, manage, and retrieve Docker images locally without relying on public registries like Docker Hub.

The project showcases a practical **DevOps workflow**, focusing on containerization, image management, and security.

---

## 🎯 Objectives
- Understand Docker and containerization concepts  
- Create a private Docker registry  
- Implement authentication using `htpasswd`  
- Push and pull Docker images securely  
- Verify stored images using registry APIs  

---

## 🛠️ Technologies Used
- Docker  
- Ubuntu (WSL)  
- Docker Registry  
- Apache htpasswd (authentication)  

---

## 🧠 Key Concepts
- **Docker Image** → A packaged application with all dependencies  
- **Docker Container** → Running instance of an image  
- **Docker Registry** → Storage system for Docker images  
- **Tagging** → Assigning a name to an image for registry storage  

---

## 🏗️ Architecture
Docker Hub → Local System → Private Registry → Push/Pull Images  

---

## ▶️ How to Run the Project
1. Open Ubuntu (WSL) terminal  
2. Install Docker  
3. Start Docker service  
4. Execute commands step-by-step  
5. Ensure Docker is running before executing commands  

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
docker pull nginx
7. Tag Image for Local Registry
docker tag nginx localhost:5000/my-nginx
8. Push Image to Private Registry
docker push localhost:5000/my-nginx
9. Pull Image from Private Registry
docker pull localhost:5000/my-nginx
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
Docker image (my-nginx) pushed and pulled successfully
Registry contents verified using API

Example Output:

{"repositories":["my-nginx"]}
🔐 Security Features
Authentication using username and password
Prevents unauthorized access
Ensures secure image storage
💡 Use Cases
Private Docker image storage
DevOps CI/CD pipelines
Secure application deployment
Internal organizational use
📈 Future Enhancements
Add HTTPS using SSL certificates
Deploy registry on cloud platforms
Integrate with CI/CD tools
Implement role-based access control
🎤 Conclusion

This project demonstrates the implementation of a secure private Docker registry for efficient and controlled management of Docker images, reflecting real-world DevOps practices.

👩‍💻 Author

Anuja Shinde
