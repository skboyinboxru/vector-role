# Ansible Role: Vector

Устанавливает и настраивает Vector (log collector) для CentOS 7.

## Requirements

- CentOS 7
- Ansible 2.9+
- Python 3

## Role Variables

### Default Variables (`defaults/main.yml`)

| Variable | Default | Description |
|----------|---------|-------------|
| `vector_version` | `"0.28.0"` | Version of Vector to install |
| `vector_install_dir` | `"/opt/vector"` | Installation directory |
| `vector_config_dir` | `"/etc/vector"` | Configuration directory |
| `vector_bin_path` | `"/usr/local/bin/vector"` | Path to Vector binary |
| `vector_user` | `"vector"` | System user for Vector |
| `vector_group` | `"vector"` | System group for Vector |
| `clickhouse_host` | `"localhost"` | ClickHouse server host |
| `clickhouse_port` | `8123` | ClickHouse HTTP port |
| `clickhouse_database` | `"default"` | ClickHouse database name |
| `clickhouse_table` | `"logs"` | ClickHouse table name |
| `vector_api_enabled` | `true` | Enable Vector API |
| `vector_api_address` | `"0.0.0.0:8686"` | Vector API address |

### Variable Files (`vars/main.yml`)

| Variable | Value | Description |
|----------|-------|-------------|
| `vector_download_url` | Auto-generated | Download URL for Vector |
| `vector_tmp_dir` | `"/tmp/vector-install"` | Temporary directory |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: vector_servers
  vars:
    clickhouse_host: "192.168.1.100"
    clickhouse_port: 8123
  roles:
    - vector-role
