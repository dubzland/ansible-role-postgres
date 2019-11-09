# Dubzland: PostgreSQL
[![Gitlab pipeline status (self-hosted)](https://img.shields.io/gitlab/pipeline/jdubz/dubzland-postgres?gitlab_url=https%3A%2F%2Fgit.dubzland.net)](https://git.dubzland.net/jdubz/dubzland-postgres/pipelines)

Installs and configures PostgreSQL server.

## Requirements

Ansible version 2.4 or higher.

## Role Variables

Available variables are listed below, along with their default values (see
    `defaults/main.yml` for more info):

### dubzland_postgres_version

```yaml
dubzland_postgres_version: "11"
```

Version of Postgres to install.

### dubzland_postgres_user/dubzland_postgres_group

```yaml
dubzland_postgres_user: 'postgres'
dubzland_postgres_group: 'postgres'
```

User and group PostgreSQL will run as.

### dubzland_postgres_socket_directories

```yaml
dubzland_postgres_socket_directories:
  - /var/run/postgresql
```

The directories PostgreSQL will create sockets in for local communication.

### dubzland_postgres_configuration

```yaml
dubzland_postgres_configuration:
  - option: unix_socket_directories
    value: /var/run/postgresql
  - option: listen_addresses
    value: "0.0.0.0"
```

Any configuration options that should be written to `/etc/postgresql/<version>/main/postgresql.conf`.

### dubzland_postgres_locales

```yaml
dubzland_postgres_locales:
  - 'en_US.UTF-8'
```

Any locales that should be generated to be used by PostgreSQL.

### dubzland_postgres_hba_entries

```yaml
dubzland_postgres_hba_entries:
  - type: local
    database: all
    user: postgres
    auth_method: peer
  - type: local
    database: all
    user: all
    auth_method: peer
  - type: host
    database: all
    user: all
    address: '127.0.0.1/32'
    auth_method: md5
  - type: host
    database: all
    user: all
    address: '::1/128'
    auth_method: md5
```

Host based authentication entries for `pg_hba.conf`.  Default values mirror a
fresh install.

### dubzland_postgres_users

```yaml
dubzland_postgres_users: []
```

Any users that should be created on the server.  See `defaults/main.yml` for
details.

### dubzland_postgres_databases

```yaml
dubzland_postgres_databases: []
```

Any databases that should be created on the server.  See `defaults/main.yml` for
details.

### dubzland_postgres_extensions

```yaml
dubzland_postgres_extensions: []
```

Any extensions that should be enabled on the server.  See `defaults/main.yml` for
details.

## Dependencies

None

## Example Playbook

```yaml
- hosts: db-servers
  become: yes
  roles:
  - role: dubzland-postgres
```

## License

MIT

## Author

* [Josh Williams](https://codingprime.com)
