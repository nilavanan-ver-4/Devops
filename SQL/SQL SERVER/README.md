# SQL Server Docker Setup with Docker Compose

This repository contains a Docker Compose configuration to quickly set up **Microsoft SQL Server 2022** in a containerized environment for local development and testing.

---

## 📦 Contents

- `sqlserver-compose.yml` – Docker Compose file for running SQL Server
- `README.md` – Setup, installation, and usage instructions

---

## ✅ Prerequisites

Before using this setup, ensure the following are installed on your system:

- [Docker](https://www.docker.com/products/docker-desktop/)
- [Docker Compose](https://docs.docker.com/compose/)
- Optional (for command-line access): [sqlcmd tools](https://learn.microsoft.com/en-us/sql/tools/sqlcmd-utility)

---

## 🔐 Default SQL Server Credentials

| Parameter     | Value            |
|---------------|------------------|
| **Username**  | `sa`             |
| **Password**  | `bornNila24*4`   |
| **Port**      | `1433`           |

> ⚠️ **Note:** These credentials are hardcoded for development use. **Do not** use them in production.

---

## 🚀 Getting Started

### 1. Create Project Folder

```bash
mkdir sqlserver-docker
cd sqlserver-docker
```

Create a file named `sqlserver-compose.yml` and paste in the Docker Compose content.

### 2. Start SQL Server

```bash
docker compose -f sqlserver-compose.yml up -d
```

This will download the latest SQL Server 2022 image and start the container in the background.

---

## 🔌 Connecting to SQL Server

### Option 1: SQL Server Management Studio (SSMS)

- **Server name:** `localhost,1433`
- **Authentication:** SQL Server Authentication
- **Login:** `sa`
- **Password:** `bornNila24*4`

### Option 2: Command Line with `sqlcmd`

```bash
sqlcmd -S localhost -U sa -P "bornNila24*4"
```

Example query inside `sqlcmd`:

```sql
SELECT @@VERSION;
GO
```

---

## 🔧 Managing the Container

| Command                           | Description                       |
| --------------------------------- | --------------------------------- |
| `docker ps`                       | Check if the container is running |
| `docker compose down`             | Stop the container                |
| `docker compose down -v`          | Stop and delete all volumes       |
| `docker logs sqlserver_container` | View container logs               |

---

## 📂 Data Persistence

The SQL Server container uses a Docker volume (`sqlserver_data`) to persist database files across restarts and shutdowns.

---

## 🛡 Security Notice

- This setup is for **local development only**.
- Never expose the container to the internet without firewall, SSL, and strong authentication.
- Rotate the `SA_PASSWORD` regularly in production systems.

---

## 🧽 Cleanup

To stop and remove the container and associated volumes:

```bash
docker compose -f sqlserver-compose.yml down -v
```

---

## 📄 License

This project is provided without warranty for development purposes only. You are responsible for securing your deployment in production.

---

**Optional improvements:**

- Add a `.env` file for credentials instead of hardcoding them  
- Include database seeding scripts (e.g., to create tables or users)
- Package this into a downloadable `.zip`

Let me know if you’d like