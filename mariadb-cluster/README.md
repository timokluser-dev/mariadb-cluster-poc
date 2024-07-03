# mariadb-cluster

Standalone MariaDB instance.

## Setup

```bash
cp -n .env.dist .env

# update .env

docker network create --internal mariadb-cluster-data-net

docker compose up -d
```

## Usage

Add containers to `mariadb-cluster` network.

### Create User & DB

```sql
CREATE USER 'service'@'localhost' IDENTIFIED BY 'password';
--- ALL HOSTS:
--- CREATE USER 'service'@'%' IDENTIFIED BY 'password';

CREATE DATABASE IF NOT EXISTS db_name;

GRANT ALL PRIVILEGES ON db_name.* TO 'service'@'localhost';

FLUSH PRIVILEGES;
```

## Management Access

Edit .env `LISTENING_IP` to any IP (e.g. local network or tailscale)

⚠️ Change back to 127.0.0.1 after changes were made
