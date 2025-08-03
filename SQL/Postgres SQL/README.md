# PostgreSQL Docker Setup with Docker Compose

This project provides a ready-to-run Docker Compose setup to run PostgreSQL 16 for development and testing in a containerized environment.

---

## 📦 Contents

- `postgres-compose.yml` – Docker Compose file to run PostgreSQL
- `README.md` – Setup guide, connection instructions, and security notes

---

## ✅ Prerequisites

Ensure the following are installed on your system:

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/)
- Optional (for command-line access): [psql CLI](https://www.postgresql.org/download/)

---

## 🔐 Default PostgreSQL Configuration

| Parameter    | Value          |
|--------------|----------------|
| **User**     | `nila2003`     |
| **Password** | `bornNila24*4` |
| **Database** | `nila_db`      |
| **Port**     | `5432`         |

> ⚠️ **Important:** These credentials are intended for **local use only**. Please secure or change them in production.

---

## 🚀 Setup Instructions

### 1. Create Project Folder

```bash
mkdir postgres-docker
cd postgres-docker
```

Create a file named `postgres-compose.yml` and paste the Docker Compose content.

### 2. Start PostgreSQL Server

```bash
docker compose -f postgres-compose.yml up -d
```

### 3. Confirm the container is running

```bash
docker ps
```

You should see `postgres_container` running.

---

## 🔌 Connecting to PostgreSQL

### Option 1: Using a GUI Client (DBeaver, pgAdmin, TablePlus, etc.)

- **Host:** `localhost`
- **Port:** `5432`
- **Username:** `nila2003`
- **Password:** `bornNila24*4`
- **Database:** `nila_db`

### Option 2: Using `psql` CLI

If `psql` is installed:

```bash
psql -h localhost -p 5432 -U nila2003 -d nila_db
```

Enter the password when prompted.

Example SQL query:

```sql
SELECT version();
```

---

## 🔧 Managing the Container

| Command                          | Description                  |
| -------------------------------- | ---------------------------- |
| `docker compose down`            | Stop the container           |
| `docker compose down -v`         | Stop and remove data volumes |
| `docker logs postgres_container` | View logs from the container |

---

## 📂 Data Persistence

A named Docker volume (`postgres_data`) is used to persist PostgreSQL data between container restarts.

---

## 🛡 Security Notice

- This configuration is **not intended for production use** without modification.
- Never expose your PostgreSQL port publicly without firewalls, SSL, or password hardening.
- Change the default credentials and manage environment variables securely.

---

## 🧽 Cleanup

To completely remove containers, network, and volumes:

```bash
docker compose -f postgres-compose.yml down -v
```

---

## 📄 License

This is provided as a development resource. Use it at your own risk in production environments.

---

**Optional improvements:**

- Create a `.env` file to hide credentials
- Add SQL seed/init scripts
- Zip both the SQL Server and PostgreSQL setups for download

Let me know if you want to implement any of