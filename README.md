# DevOps Engineer Assignment

## Task 1: Deploy a Systemd Service

### Objective
Demonstrate the ability to deploy and manage a service on a Linux system.

### Steps
1. Create a simple application (e.g., a Python or Node.js HTTP server).
2. Write a systemd unit file to manage the application as a service.
3. Ensure the service starts automatically on boot and logs output to a file.

### Solution
1. Create `task1` directory:
   ```bash
   sudo mkdir task1
   ```
2. Change owner and set permissions:
   ```bash
   sudo chown -R ubuntu:ubuntu /home/ubuntu/task1
   sudo chmod 755 /home/ubuntu/task1
   ```
3. Create a simple application file:
   ```bash
   sudo vim task1.js
   ```
4. Display `task1.js` content:
   ```bash
   cat task1.js
   ```
5. Create `task1.service` in `/etc/systemd/system`:
   ```bash
   sudo vim task1.service
   ```
6. Display `task1.service` content:
   ```bash
   sudo cat /etc/systemd/system/task1.service
   ```
7. Create log files:
   ```bash
   sudo touch /var/log/task1.log /var/log/task1_error.log
   ```
8. Change owner and set permissions of log files:
   ```bash
   sudo chown ubuntu:ubuntu /var/log/task1.log /var/log/task1_error.log
   sudo chmod 644 /var/log/task1.log /var/log/task1_error.log
   ```
9. Restart systemd and reload the `task1.service`:
   ```bash
   sudo systemctl daemon-reload
   sudo systemctl restart task1.service
   sudo systemctl status task1.service
   ```
10. Check service status and log output:
    ```bash
    sudo systemctl status task1.service
    cat /var/log/task1.log
    cat /var/log/task1_error.log
    ```
11. Ensure the service starts automatically on boot.

---

## Task 2: Docker-Based Application Deployment

### Objective
Showcase containerization and deployment skills.

### Steps
1. Containerize the application from Task 1 using Docker.
2. Create a `docker-compose.yml` file to manage the application and a reverse proxy (e.g., NGINX or Traefik) for load balancing.
3. Ensure high availability by configuring at least 2 replicas.

### Solution
1. Create `task2` directory.
2. Install Docker.
3. Ensure Docker is successfully installed.
4. Create a simple application in the `task2` directory.
5. Initialize `package.json` file.
6. Install `express`:
   ```bash
   npm install express
   ```
7. Create `Dockerfile`.
8. Create `docker-compose.yaml` with 2 replicas configured.
9. Create `nginx.conf` file.
10. Install Docker Compose.
11. Run the application:
    ```bash
    docker-compose up
    ```
12. Check if containers are working properly.
13. Verify the public IP address of the EC2 instance.

---

## Task 3: Kubernetes Cluster Setup

### Objective
Validate experience with Kubernetes and high-availability configurations.

### Steps
1. Deploy the application on a Kubernetes cluster.
2. Use a tool like `kubectl`, Helm, or Kustomize for deployment.
3. Ensure the application is reachable via a LoadBalancer or Ingress.
4. Demonstrate rolling updates for the application.

### Solution
1. Create `task3` directory.
2. Create a Kubernetes deployment file (`deployment.yaml`).
3. Deploy the application:
   ```bash
   kubectl apply -f deployment.yaml
   ```
4. Create a LoadBalancer service (`service.yaml`) to expose the application:
   ```bash
   kubectl apply -f service.yaml
   ```
5. Demonstrate rolling updates:
   - Change NGINX version from `latest` to `alpine`.
   - Deploy the updated application.
   - Monitor the rollout.

---

## Task 4: Debugging and Troubleshooting

### Objective
Assess problem-solving skills.

### Scenario
You are provided with a misconfigured systemd service or Kubernetes Deployment.

### Steps
1. Identify and fix the issues.
2. Document your troubleshooting process.

### Solution
1. Incorrect file location for `task1.js` was identified.
2. Reload systemd to recognize the new unit file:
   ```bash
   sudo systemctl daemon-reload
   ```
3. Enable the service to start on boot:
   ```bash
   sudo systemctl enable task1.service
   ```
4. Start the service:
   ```bash
   sudo systemctl start task1.service
   ```
5. Check the error log file and fix the file location.
6. Verify if the service is working correctly.

---

**Author:** Yusuf Teoman Bayoğlu
