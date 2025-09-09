
# 🛡️ PostgreSQL Security Cheat Sheet (Beginner-Friendly)

📝 *Learning Note:* I'm not a DBA. I'm just learning by doing and sharing what worked for me in practice.  
📦 Tested on: Ubuntu Server 22.04 + PostgreSQL 16

---

## 1. Separate Development and Production

**Why:** Avoid mixing test and real data. Prevent accidents.

```bash
# Update and install dependencies
sudo apt-get update
sudo apt-get install wget gnupg lsb-release -y

# Add official PostgreSQL repo (with GPG verification)
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
sudo apt-get update

# Install PostgreSQL
sudo apt-get install postgresql-16 -y

# Check version
sudo -u postgres psql -c "SELECT version();"
```

---

## 2. Don't Use the Superuser in Your App

**Why:** Limit damage if your app or server is compromised.

```bash
# Switch to PostgreSQL user
sudo -i -u postgres

# Create database
createdb database_name

# Enter PostgreSQL shell
psql

-- Create a limited app user
CREATE USER database_user WITH PASSWORD 'secure_password';
GRANT CONNECT ON DATABASE database_name TO database_user;

-- Create an admin user
CREATE USER user_admin WITH PASSWORD 'secure_password';
GRANT CONNECT ON DATABASE database_name TO user_admin;

-- Grant permissions to admin user
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO user_admin;

-- Ensure future tables inherit permissions
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO user_admin;

\q
```

---

## 3. Configure `pg_hba.conf` Securely

**Why:** Prevent unauthorized remote access.

```bash
# Edit postgresql.conf
sudo vi /etc/postgresql/16/main/postgresql.conf

# Inside:
listen_addresses = 'localhost,APP_SERVER_IP'  # Only allow trusted IPs

# Edit pg_hba.conf
sudo vi /etc/postgresql/16/main/pg_hba.conf

# Add rules like:
# TYPE   DATABASE       USER        ADDRESS             METHOD
host     database_name  user_admin  YOUR_PC_IP/32        md5
host     database_name  user_app    APP_SERVER_IP/32     md5
```

### 🔍 pg_hba.conf Cheat Table

| Column     | Example               | Description                          |
|------------|------------------------|--------------------------------------|
| TYPE       | `host`, `local`        | Connection type                      |
| DATABASE   | `all`, `database_name` | Which DB(s) to allow                 |
| USER       | `all`, `user_app`      | PostgreSQL user(s)                   |
| ADDRESS    | `127.0.0.1/32`         | Who can connect (IP/Subnet)          |
| METHOD     | `md5`, `scram-sha-256` | Authentication method                |

**⚠️ Dangerous values to avoid:**  
- `0.0.0.0/0` → Any IP (public access!)  
- `trust` → No password required  

```bash
# Restart PostgreSQL after changes
sudo systemctl restart postgresql
```

---

## 4. Backups (and Test Restores)

**Why:** A backup you can’t restore is useless.

```bash
# Create backup
pg_dump -U database_user database_name > backup.sql

# Test restore
createdb test_restore
psql -U database_user test_restore < backup.sql
```

---

## 5. Why It Matters

Even with Supabase/Firebase/etc., these concepts help you:

✅ Avoid giving root access to everything  
✅ Protect against accidental data loss  
✅ Build habits that scale into production setups

---

## ✅ Quick Summary

| Step                         | Purpose                              |
|------------------------------|--------------------------------------|
| Separate dev & prod DBs      | Avoid accidental data mixing         |
| Use limited users            | Minimize risk from compromised app   |
| Configure `pg_hba.conf`      | Restrict DB access to known IPs      |
| Make and test backups        | Ensure disaster recovery works       |

---

📌 *Reminder:* This is just the starting point. Security is an ongoing process, and there’s always more to learn.

🙏 If you’re an experienced PostgreSQL user or DBA, feel free to suggest improvements!
