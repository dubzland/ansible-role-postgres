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
dubzland_postgres_version: ""
```

Version of Postgres to install (formatted according to the platform's version scheme)

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
