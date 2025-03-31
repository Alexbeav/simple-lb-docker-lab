# 🧪 Simple Load Balancer Lab (Docker + HAProxy)

This lab simulates a basic load-balanced environment using **Docker**, **HAProxy**, and **Apache web servers**.

It sets up:
- Two web servers (`web1`, `web2`) running Apache with custom HTML pages
- One load balancer (`lb`) running HAProxy
- A stats page to monitor live traffic
- Everything runs on a custom Docker bridge network

---

## ⚙️ Architecture

```
               +-------------+
               |   HAProxy   | (http://localhost:8080)
               |    (lb)     | (http://localhost:8084 - Stats page)
               +------+------+                  
                      |
     +----------------+----------------+
     |                                 |
+----+----+                     +------+----+
|  web1   |                     |   web2     |
| :8081   |                     |  :8082     |
+---------+                     +------------+
```

---

## 📦 Technologies Used

- Docker
- Docker Compose
- HAProxy (as reverse proxy/load balancer)
- Apache HTTPD
- Custom HTML/CSS pages for clear identity
- HAProxy Stats UI (http://localhost:8404)

---

## 🚀 How to Run

### 1. Clone the Repo

```bash
git clone https://github.com/Alexbeav/simple-lb-docker-lab.git
cd simple-lb-docker-lab
```

### 2. Start the Lab

```bash
docker-compose up --build -d
```

---

## 🔍 What to Expect

- Access the HAProxy load balancer at: [http://localhost:8080](http://localhost:8080)
- See traffic split between `web1` and `web2` (alternating responses)
- Access the HAProxy stats page at: [http://localhost:8404](http://localhost:8404)
  - **Username**: `admin`
  - **Password**: `admin`

---

## 📄 Folder Structure

```
simple-lb-docker-lab/
├── docker-compose.yml
├── haproxy.cfg
├── web1/
│   ├── Dockerfile
│   └── index.html
├── web2/
│   ├── Dockerfile
│   └── index.html
├── .gitignore
```

---

## 🧠 Next Steps

- Add more web replicas and scale horizontally
- Move to Kubernetes for orchestration and service discovery
- Add ingress controllers or TLS with certbot

---

## 👨‍💻 Author

Built as a modern DevOps lab for experimenting with container-based load balancing.
