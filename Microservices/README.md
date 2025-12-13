# Microservices Kubernetes Deployment Assessment

  ## Objective:
 
      Deploy a microservices application on Kubernetes using Minikube, ensuring proper service communication and configuration.
---
  ## Microservices Included
  
  | Service          | Description                         | Port |
  |------------------|-------------------------------------|------|
  | User Service     | Provides user-related data          | 3000 |
  | Product Service  | Provides product-related data       | 3001 |
  | Order Service  | Provides product-related data         | 3002 |
  | Gateway Service  | Acts as API Gateway (reverse proxy) | 3003 |

---

 ## Folder Structure (Final)
     
     K8s/
     ├── deployments/
     │   ├── user-deployment.yaml
     │   ├── product-deployment.yaml
     │   ├── order-deployment.yaml
     │   └── gateway-deployment.yaml
     ├── services/
     │   ├── user-service.yaml
     │   ├── product-service.yaml
     │   ├── order-service.yaml
     │   └── gateway-service.yaml
     ├── ingress/
     │   └── ingress.yaml
     ├── screenshots/
     │   ├── pods.png
     │   ├── logs.png
     │   └── service-test.png
     └── README.md
     
---


 ## Create Kubernetes Deployment manifests for all services:

   <img width="1027" height="617" alt="image" src="https://github.com/user-attachments/assets/5ff40878-6fc5-4688-8c85-34e67f62815f" />

---

 ## Create corresponding Service resources:
 

   <img width="1100" height="738" alt="image" src="https://github.com/user-attachments/assets/03a721ba-eafd-471f-a4e7-9fadc366f2a9" />
   
---

 ## Minikube Setup and Validation:
   
   ## Prerequisites:
   
     Ensure the following are installed on your system:
     1.Docker Desktop (Windows)
     2.kubectl CLI

   ## Enable Kubernetes in Docker Desktop

     1.Open Docker Desktop
     2.Go to Settings → Kubernetes
     3.Enable Kubernetes
     4.Click Apply & Restart
     5.Wait until Kubernetes status shows Running

   <img width="1917" height="917" alt="image" src="https://github.com/user-attachments/assets/9b35de4c-55d6-475e-983f-83eeeaed4c17" />

---

 ## Documentation and Testing:
    
   ## Deployment process:
     Deployed to default service
      1.Deploy Microservices:
         kubectl apply -f deployments/
 
      2.Create Services:
         kubectl apply -f services/
 

   ## Verify Resources:
       kubectl get pods 
  
   <img width="698" height="142" alt="image" src="https://github.com/user-attachments/assets/ae2893f1-c78e-4d3c-815a-20eaecf46f00" />


       kubectl get svc 

   <img width="742" height="165" alt="image" src="https://github.com/user-attachments/assets/e2ef2b47-12d3-44f0-affc-bb4e050ebeff" />

---

 ## Bonus Task: Ingress Configuration (Optional)
    
   ## Install NGINX Ingress Controller:

       kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.2/deploy/static/provider/cloud/deploy.yaml

       kubectl get svc -n ingress-nginx

   <img width="1096" height="95" alt="image" src="https://github.com/user-attachments/assets/1dd1b4f0-155a-458f-a1ec-82cc451b50d9" />


  ## Apply Ingress:
         
         kubectl apply -f ingress/ingress.yaml

         kubectl get ingress

   <img width="742" height="76" alt="image" src="https://github.com/user-attachments/assets/645209ff-f8a4-4e73-a68e-f0e36288e524" />

---
      
 ## Service Testing:

   Without port forward apis are working.

   
   http://localhost/api/users
   
 <img width="633" height="246" alt="image" src="https://github.com/user-attachments/assets/b19d4d7b-e0a6-4dc5-8251-4769e854755f" />


   http://localhost/api/products

 <img width="838" height="245" alt="image" src="https://github.com/user-attachments/assets/65154cfd-2eac-46d4-a4e3-8926b1dc5642" />

   http://localhost/api/orders

 <img width="853" height="253" alt="image" src="https://github.com/user-attachments/assets/241ea7e7-26db-4d72-a71e-a62009818ba1" />

---



   










 



