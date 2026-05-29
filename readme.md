# NGINX Reverse Proxy & Load Balancer with Docker

## Overview

This project demonstrates how to configure **NGINX as a Reverse Proxy and Load Balancer** for multiple Docker containers. It also includes custom domain configuration and SSL certificate generation using **Let's Encrypt (Certbot)**.

## Architecture

```text
Internet
   │
   ▼
NGINX Load Balancer
   │
   ├── Website 1
   │
   └── Website 2
```

## Features

* NGINX Reverse Proxy
* Load Balancing
* Docker Compose Orchestration
* Custom Domain Mapping
* HTTPS with Let's Encrypt SSL
* Container Networking

## Project Structure

```text
docker-nginx/
│
├── website1/
│   ├── Dockerfile
│   └── index.html
│
├── website2/
│   ├── Dockerfile
│   └── index.html
│
├── nginx/
│   └── nginx.conf
│
├── certbot/
│   ├── conf/
│   └── www/
│
└── docker-compose.yml
```

## Prerequisites

* Linux Server / VM
* Docker
* Docker Compose
* Domain Name
* NGINX
* Certbot

## Docker Commands Used

### Build and Start Containers

```bash
docker compose up -d
```

### Check Running Containers

```bash
docker ps
```

### View Logs

```bash
docker logs nginx-lb
```

### Restart NGINX Container

```bash
docker restart nginx-lb
```

### Execute Commands Inside Container

```bash
docker exec -it nginx-lb bash
```

## SSL Certificate Generation

### Generate SSL Certificate

```bash
docker run --rm \
-v $(pwd)/certbot/conf:/etc/letsencrypt \
-v $(pwd)/certbot/www:/var/www/certbot \
certbot/certbot certonly \
--webroot \
--webroot-path=/var/www/certbot \
--email your-email@example.com \
--agree-tos \
--no-eff-email \
-d your-domain.com
```

### Renew Certificates

```bash
docker run --rm \
-v $(pwd)/certbot/conf:/etc/letsencrypt \
-v $(pwd)/certbot/www:/var/www/certbot \
certbot/certbot renew
```

## Useful Linux Commands

### Check DNS Resolution

```bash
nslookup your-domain.com
```

### Test Website

```bash
curl http://your-domain.com
```

### Verify NGINX Configuration

```bash
docker exec nginx-lb nginx -t
```

### Reload NGINX

```bash
docker exec nginx-lb nginx -s reload
```

## Learning Outcomes

Through this project I gained hands-on experience with:

* NGINX Reverse Proxy
* Load Balancing
* Docker Networking
* Docker Compose
* SSL/TLS Certificates
* Let's Encrypt & Certbot
* DNS Configuration
* Linux Administration

## Author

Aman Yadav

GitHub: https://github.com/aman82005
