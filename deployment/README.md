# Deployment Guide

## Server Setup

1. Update system packages:

```bash
sudo apt update && sudo apt upgrade -y
```

2. Install required packages:

```bash
sudo apt install python3-pip python3-venv nginx -y
```

## Application Setup

1. Clone the repository:

```bash
git clone https://github.com/Daniel-T-Dada/hng-stage2-task-fastapi.git
cd hng-stage2-task-fastapi
```

2. Create and activate virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

## Nginx Setup

1. Copy Nginx configuration:

```bash
sudo cp nginx/fastapi_app.conf /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/fastapi_app.conf /etc/nginx/sites-enabled/
```

2. Test and restart Nginx:

```bash
sudo nginx -t
sudo systemctl restart nginx
```

## Service Setup

1. Copy service file:

```bash
sudo cp deployment/fastapi.service /etc/systemd/system/
```

2. Start and enable service:

```bash
sudo systemctl start fastapi
sudo systemctl enable fastapi
```

## Verify Deployment

1. Check service status:

```bash
sudo systemctl status fastapi
```

2. Test the API:

```bash
curl http://localhost/api/v1/books/1
```
