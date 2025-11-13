# Securepoint UTM Beszel Agent Ansible Role

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-sp__utm__beszel-blue.svg)](https://galaxy.ansible.com/ui/standalone/roles/Primexz/sp_utm_beszel/)

An Ansible role that installs and configures the [Beszel](https://github.com/henrygd/beszel) monitoring agent on a Securepoint UTM.

## Requirements

- Ansible 2.9 or higher
- Target system: Securepoint UTM (Linux-based)
- Network access to download the Beszel agent binary from GitHub releases
- Root user privileges

## Role Variables

### Required Variables

These variables must be set for the role to function properly:

| Variable | Type | Description |
|----------|------|-------------|
| `beszel_key` | string | SSH public key for authentication between the agent and Beszel server. This is displayed in the Beszel web interface when adding a new system. |
| `beszel_port` | integer | Port number for the agent to listen on. This is displayed in the Beszel web interface when adding a new system. |

### Optional Variables

These variables have default values and can be customized as needed:

| Variable | Default | Type | Description |
|----------|---------|------|-------------|
| `beszel_version` | `"v0.16.0"` | string | Version of Beszel agent to install. Should match a valid GitHub release tag. |
| `beszel_extra_filesystems` | `""` | string | Additional filesystems to monitor (e.g., `"sdb"` for a second disk). Leave empty to monitor only the root filesystem. |
| `beszel_root_filesystem` | `""` | string | Specify the root filesystem device if auto-detection fails. Usually not needed. |
| `beszel_primary_temp_sensor` | `""` | string | Specify the primary temperature sensor to monitor. If not set, Beszel will auto-detect the sensor. |
| `beszel_temp_sensors` | `""` | string | Whitelist or blacklist temperature sensors for monitoring. Use comma-separated values to specify which sensors to include or exclude. |
| `beszel_home_dir` | `"/root/beszel-agent"` | string | Directory where the Beszel agent binary will be installed. |
| `beszel_download_url` | `"https://github.com/henrygd/beszel/releases/download"` | string | Base URL for downloading Beszel releases. |
| `beszel_binary_name` | `"beszel-agent_linux_amd64.tar.gz"` | string | Name of the binary archive to download. |

## Dependencies

This role has no external dependencies.

## Example Playbook

```yaml
- name: Deploy beszel monitoring agent
  hosts: all
  become: true
  roles:
    - role: Primexz.sp_utm_beszel
      vars:
        beszel_key: "ssh-ed25519 EXAMPLE123..."
        beszel_port: 12345
```

## License

This project is licensed under the [MIT License](LICENSE).