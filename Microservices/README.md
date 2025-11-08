# Microservices Containerization using Node.js, Docker & Docker Compose

 ## Objective:
 
        Containerize a microservices-based Node.js application using **Docker** and orchestrate them using **Docker Compose**.

---
  ## Microservices Included
  
  | Service          | Description                         | Port |
  |------------------|-------------------------------------|------|
  | User Service     | Provides user-related data          | 3000 |
  | Product Service  | Provides product-related data       | 3001 |
  | Order Service  | Provides product-related data         | 3002 |
  | Gateway Service  | Acts as API Gateway (reverse proxy) | 3003 |

---

  ##  Directory Structure (Required for Submission)
     
    ├── user-service/
    │ └── Dockerfile
    ├── product-service/
    │ └── Dockerfile
    ├── order-service/
    │ └── Dockerfile
    ├── gateway-service/
    │ └── Dockerfile
    ├── docker-compose.yml
    └── README.md
   Each service contains a Dockerfile with:
    
   **Dockerfile**
   
    FROM node:20-alpine
    
    WORKDIR /app
    
    COPY package*.json ./
    RUN npm install --production
    
    COPY . .
    
    EXPOSE 3000  
    Only the port number changes based on the microservice.
    
    CMD ["node", "app.js"]

  **docker-compose.yml**

   All services are orchestrated using Docker Compose:
   
    name: microservices-task

    networks:
      appnet:
        driver: bridge
    
    services:
      user-service:
        build:
          context: C:\Users\microservices\Microservices-Task\Microservices\user-service
          dockerfile: Dockerfile
        container_name: user-service
        ports:
          - "3000:3000"
        environment:
          - NODE_ENV=production
        networks:
          - appnet
    
      product-service:
        build:
          context: C:\Users\microservices\Microservices-Task\Microservices\product-service
          dockerfile: Dockerfile
        container_name: product-service
        ports:
          - "3001:3001"
        environment:
          - NODE_ENV=production
        networks:
          - appnet
    
      order-service:
        build:
          context: C:\Users\microservices\Microservices-Task\Microservices\order-service
          dockerfile: Dockerfile
        container_name: order-service
        ports:
          - "3002:3002"
        environment:
          - NODE_ENV=production
        networks:
          - appnet
        depends_on:
          - user-service
          - product-service
    
      gateway:
        build:
          context: C:\Users\microservices\Microservices-Task\Microservices\gateway-service
          dockerfile: Dockerfile
        container_name: gateway
        ports:
          - "3003:3003"
        environment:
          - NODE_ENV=production
          # If your gateway reads these to route internally, keep them:
          - USERS_URL=http://user-service:3000
          - PRODUCTS_URL=http://product-service:3001
          - ORDERS_URL=http://order-service:3002
        networks:
          - appnet
        depends_on:
          - user-service
          - product-service
          - order-service
---

  ##  Start services using Docker Compose
     
     docker compose up --build

  <img width="1382" height="945" alt="image" src="https://github.com/user-attachments/assets/0bf5b2f0-8664-4c7d-99a2-e3f1a8f5f7cc" />

  <img width="1918" height="962" alt="image" src="https://github.com/user-attachments/assets/bb8369bb-56c6-43e7-b49a-048c912458c2" />

---

  ##  How to test each service

 | Service           | Description                       |
 |-------------------|-----------------------------------|
 | User Service	     |   http://localhost:3000/users     |
 | Product Service	 |   http://localhost:3001/products  |
 |  Order Service  	 |   http://localhost:3002/orders    |
 | API Gateway	     |   http://localhost:3003/api/users |
 

<img width="662" height="272" alt="image" src="https://github.com/user-attachments/assets/d115975e-c507-4a89-8a18-b95f9f3be6f5" />


<img width="807" height="331" alt="image" src="https://github.com/user-attachments/assets/9cf8f852-fe97-41cb-87d0-80f6472aadcf" />


<img width="592" height="257" alt="image" src="https://github.com/user-attachments/assets/7b1e024f-2f77-4a18-868c-c626d2ed3d4b" />

---


**This is Gateway level:**

---

http://localhost:3003/api/users

<img width="711" height="277" alt="image" src="https://github.com/user-attachments/assets/1c9131fc-f01b-4324-8805-5df2a0e10233" />

http://localhost:3003/api/products

<img width="837" height="257" alt="image" src="https://github.com/user-attachments/assets/9aef168f-3e87-4cb0-8751-5b4d48635c74" />

http://localhost:3003/api/orders

<img width="556" height="233" alt="image" src="https://github.com/user-attachments/assets/44c96884-f4c6-4743-95d3-255744488393" />

---

##  Push the code to Github
  
  git add .
  
  git status
  
  
  <img width="751" height="308" alt="image" src="https://github.com/user-attachments/assets/684b38ec-cb88-4788-9e79-899f378ee77a" />
  
  
---

git commit -m "message"

  <img width="862" height="228" alt="image" src="https://github.com/user-attachments/assets/58e1eeda-1341-43d5-9f1f-07029994c999" />

  
---  

git push orgin main

  <img width="872" height="255" alt="image" src="https://github.com/user-attachments/assets/866d8be6-f3eb-475d-a7fc-ce8db801f6c9" />

---

<img width="1838" height="882" alt="image" src="https://github.com/user-attachments/assets/c8944722-c27d-451d-90e6-00cb34fc6377" />










 



