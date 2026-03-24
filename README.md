# Ansible Role: Radix Nginx

Sets up Nginx as a reverse proxy for Radix Babylon nodes with SSL, HTTP basic auth, and P2P port configuration.

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `nginx_release` | `1.0.9` | Babylon nginx config release version |
| `nginx_node_type` | `fullnode` | Node type (`fullnode` or `validator`) |
| `nginx_secrets_dir` | `/etc/nginx/secrets` | Nginx secrets directory |
| `nginx_cache_dir` | `/var/cache/nginx/radixdlt-hot` | Nginx cache directory |

### Required variables (from host_vars)

- `radixnode_p2p_broadcast_port` - P2P broadcast port (default: 30000)
- `radixnode_p2p_listen_port` - P2P listen port (default: 30001)
- `nginx_admin_password` - Admin basic auth password
- `nginx_metrics_password` - Metrics basic auth password
- `nginx_superadmin_password` - Superadmin basic auth password

## Example Playbook

```yaml
- hosts: radixnode
  become: true
  roles:
    - role: nginx
      vars:
        nginx_node_type: validator
```

## License

MIT
