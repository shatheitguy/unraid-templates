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
| Image | `ghcr.io/shatheitguy/it-vault` (amd64 and arm64) |
| WebUI | port 5000 |
| Paths | `/app/data`, `/app/invoices`, `/app/backups` |
| Project | https://shatheitguy.github.io/it-vault/ |
| Support | https://github.com/shatheitguy/it-vault/issues |

`it-vault.xml` is generated from
[`unraid/it-vault.xml`](https://github.com/shatheitguy/it-vault/blob/main/unraid/it-vault.xml)
in the application repository, where a test checks it against the code: every
variable it sets is one the app reads, and every path it mounts is one the app
writes. Edit it there, not here.
