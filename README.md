<!-- BEGIN_ANSIBLE_DOCS -->
<!--
Do not edit README.md directly!

This file is generated automatically by aar-doc and will be overwritten.

Please edit meta/argument_specs.yml instead.
-->
# mailpit

mailpit role for Proserver

## Supported Operating Systems

- Debian 12, 13
- Ubuntu 24.04, 22.04
- FreeBSD [Proserver](https://infrastructure.punkt.de/de/produkte/proserver.html)

## Role Arguments



#### Options for `mailpit`

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| `domain` | The domain name for the Mailpit UI. If not set, defaults to the server's FQDN or IP. | str | no |  |
| `dehydrated` |  | dict of 'dehydrated' options | no |  |
| `nginx` | Nginx configuration for Mailpit. | dict of 'nginx' options | no |  |
| `bind_addr` | The IP address Mailpit should bind for the UI and SMTP. | str | no | 127.0.0.1 |
| `smtp_port` | The port Mailpit should listen on for SMTP traffic. | int | no | 1025 |
| `ui_port` | The port Mailpit should listen on for the Web UI. | int | no | 8025 |
| `oauth2_proxy` | Name of the oauth2_proxy instance to use for authentication (optional). | str | no |  |
| `install_dir` | Directory where Mailpit will be installed (Linux only) | str | no | /opt/mailpit |
| `version` | The version of Mailpit to install (Linux only) | str | no | 1.29.1 |
| `download_url` | Download URL for the Mailpit binary. Generally auto-constructed. | str | no | https://github.com/axllent/mailpit/releases/download/v{{ mailpit.version }}/mailpit-{{ ansible_facts['system'] | lower }}-{{ 'arm64' if ansible_facts['architecture'] == 'aarch64' else 'amd64' }}.tar.gz |
| `db_path` | Path for the mailpit sqlite-database | str | no | {{ '/var/lib/mailpit/mailpit.db' if ansible_facts['system'] == 'Linux' else '/var/db/mailpit/mailpit.db' }} |

#### Options for `mailpit.dehydrated`

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| `enable` | Whether to use dehydrated for Let's Encrypt SSL certificates. | bool | no | False |

#### Options for `mailpit.nginx`

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| `enable` | Whether to configure Nginx as a reverse proxy for Mailpit. | bool | no | True |
| `bind_addr` | List of IP addresses Nginx should listen on. | list of 'str' | no | ['0.0.0.0', '[::1]'] |

## Dependencies
None.

## Installation
Add this role to the requirements.yml of your playbook as follows:
```yaml
roles:
  - name: mailpit
    src: https://github.com/punktDe/ansible-proserver-mailpit
```

Afterwards, install the role by running `ansible-galaxy install -r requirements.yml`

## Example Playbook

```yaml
- hosts: all
  roles:
    - name: mailpit
```

<!-- END_ANSIBLE_DOCS -->
