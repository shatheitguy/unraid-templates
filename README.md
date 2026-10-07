# Unraid templates — Sha The IT Guy

Community Applications templates for my own containers. One file per app, and
nothing else in here: CA scans a whole repository for templates, so an app
repository full of other XML produces a warning for every file that is not an
Unraid application. This one contains templates only.

## IT-Vault

[IT-Vault](https://github.com/shatheitguy/it-vault) is a self-hosted IT asset
register and helpdesk: assets, employees, contracts, tickets, a public request
portal, LDAP/AD sync, network scanning, printable QR labels and e-signed
handovers.

**It brings no database of its own.** Install MariaDB first (the MariaDB
template in CA is fine), create an empty database and a user for it, then
either fill in the database fields on this template or leave them empty and
let the first-run wizard ask.

```sql
CREATE DATABASE itvault CHARACTER SET utf8mb4;
CREATE USER 'itvault'@'%' IDENTIFIED BY 'a-strong-password';
GRANT ALL PRIVILEGES ON itvault.* TO 'itvault'@'%';
```

There is no default admin password: the first run asks you to create the
account.

| | |
| --- | --- |
| Image | `ghcr.io/shatheitguy/itvault` (amd64 and arm64) |
| WebUI | port 5000 |
| Paths | `/app/data`, `/app/invoices`, `/app/backups` |
| Project | https://shatheitguy.github.io/it-vault/ |
| Support | https://github.com/shatheitguy/it-vault/issues |

`it-vault.xml` is the template itself — edit it here. Keep it in step with the
app: every variable it sets must be one IT-Vault reads, and every path it
mounts must be one the app writes.

## FormCraft

[FormCraft](https://github.com/shatheitguy/formcraft) is a self-hosted form
builder: drag-and-drop forms, templates and quizzes, submissions with charts
and CSV export, users and roles, email and Telegram alerts, multilingual forms
(English, Arabic, Tamil) and full backups.

**It needs nothing else.** The template uses the built-in SQLite database in
`/mnt/user/appdata/formcraft`. To use PostgreSQL instead, create an empty
database and set *Database URL* to
`postgresql://USER:PASSWORD@HOST:5432/DBNAME?schema=public`; the same image
works with both.

There is no default admin password: the first run asks you to create the
account.

| | |
| --- | --- |
| Image | `ghcr.io/shatheitguy/formcraft` (amd64 and arm64) |
| WebUI | port 3000 |
| Paths | `/app/data` |
| Project | https://shatheitguy.github.io/formcraft/ |
| Support | https://github.com/shatheitguy/formcraft/issues |

`formcraft.xml` is the template itself — edit it here.
