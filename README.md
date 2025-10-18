# Web Server Deployment [HNG13 devOps stage0 Task]

**Author:** Dominic Ifechuku  
**Slack Username:** dom  

---

## Project Overview

This project demonstrates how to deploy a simple static webpage using **NGINX** on **Google Cloud Platform (GCP)** Compute Engine instance.  
It serves as a practical DevOps exercise designed to simulate real-world deployment and server management tasks.  

---

## Project Objectives

1. Set up and manage a GitHub repository for version control.  
2. Deploy and configure an NGINX web server on GCP.  
3. Serve a custom HTML page from the server’s public IP address.  
4. Ensure the server is accessible publicly through HTTP.

---

## Server Details

**Server Type:** GCP Compute Engine (e2-micro, Ubuntu)  
**Server Zone:** us-central1-a  
**Server IP:** 35.223.80.179 [reachable at: http://35.223.80.179]
**Web Server:** NGINX  
**Deployed Webpage:** `index.html`

## Deployment Steps

### 1. Create and Configure a GCP VM Instance

a. Navigate to **Compute Engine → VM Instances → Create Instance** in the GCP Console.  
b. Use the following settings:
   - Name: `stage-0`
   - Machine type: `e2-micro`
   - Region: `us-central1` (to remain under the GCP free tier)
   - OS: Ubuntu 25.10
   - Allow HTTP and HTTPS traffic
c. Click **Create** and wait for the instance to start.

### 2. SSH into the Instance

```bash
gcloud compute ssh stage-0 --zone=us-central1-a
```
### 3. Install NGINX

```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```
### 4. Deploy the custom webpage
Clone this Github Repository onto the VM.
```bash
sudo apt install git -y
git clone https://github.com/Dom-HTG/hng13-stage0-devops.git
cd hng13-stage0-devops
```
### 5. Copy the webpage into the NGINX web root
```bash
sudo cp index.html /var/www/html/
suco systemctl reload nginx
```
Visit http://35.223.80.179  to confirm page is live.

## Technologies Used

1. **Google Cloud Platform (GCP)** — for hosting the virtual machine

2. **NGINX** — as the web server

3. **Ubuntu 25.10** — server operating system

4. **Git & GitHub** — for source control and documentation
