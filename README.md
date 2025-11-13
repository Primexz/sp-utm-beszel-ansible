# Securepoint UTM Beszel Ansible Role

Ansible role to install and configure Beszel monitoring agent on Securepoint UTM.


## Role Variables

The following variables can be configured in `host_vars` or `group_vars`:

### Required Variables

- `beszel_key`: SSH public key for authentication with the Beszel server
  ```yaml
  beszel_key: "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBx7HLAxiWA/S8MetkpHZ4+Mb3vUpW3tNVwMpxro5V0J"
  ```

- `beszel_port`: Port for the agent to listen on (default: 45876)
  ```yaml
  beszel_port: 45876
  ```

### Optional Variables

- `beszel_extra_filesystems`: Additional filesystems to monitor (default: "")
  ```yaml
  beszel_extra_filesystems: "sdb"
  ```
- `beszel_root_filesystem`: Root filesystem to monitor (default: auto-detected)
  ```yaml
  beszel_root_filesystem: "/dev/sda1"
  ```

### System Variables (usually don't need to be changed)

- `beszel_version`: Version to install (default: "v0.16.0")
- `beszel_user`: System user for the service (default: "beszel")


### Host-specific Variables

Configure these in your host_vars files:

```yaml
---
# Required: SSH public key for authentication
beszel_key: "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBx7HLAxiWA/S8MetkpHZ4+Mb3vUpW3tNVwMpxro5V0J"

# Required: Custom port for this host
beszel_port: 45876

```

## License

MIT