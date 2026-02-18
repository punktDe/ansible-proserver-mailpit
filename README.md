<!-- BEGIN_ANSIBLE_DOCS -->
<!--
Do not edit README.md directly!

This file is generated automatically by aar-doc and will be overwritten.

Please edit meta/argument_specs.yml instead.
-->
# ansible-proserver-mailpit

mailpit role for Proserver

## Supported Operating Systems

- Debian 12, 13
- Ubuntu 24.04, 22.04
- FreeBSD [Proserver](https://infrastructure.punkt.de/de/produkte/proserver.html)

## Role Arguments



#### Options for `mailpit`

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| `domain` | The domain name for the Mailpit UI. If not set, it defaults to the server's FQDN or IP. | str | no |  |
| `use_dehydrated` | Whether to use dehydrated for Let's Encrypt SSL certificates. | bool | no | True |
| `nginx` | Nginx configuration for Mailpit. | dict of 'nginx' options | no |  |
| `bind_addr` | The IP address Mailpit should bind to (both UI and SMTP). | str | no | 127.0.0.1 |
| `smtp_port` | The port Mailpit should listen on for SMTP traffic. | int | no | 1025 |
| `ui_port` | The port Mailpit should listen on for the Web UI. | int | no | 8025 |
| `oauth2_proxy` | Name of the oauth2_proxy instance to use for authentication (optional). | str | no |  |
| `install_dir` | Directory where Mailpit will be installed. | str | no | /opt/mailpit |
| `version` | The version of Mailpit to install. | str | no | 1.29.1 |
| `amd64_linux_url` | Download URL for the Mailpit binary (Linux amd64). Generally auto-constructed. | str | no |  |

#### Options for `mailpit.nginx`

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| `bind_addr` | List of IP addresses Nginx should listen on. | list of 'str' | no | ['0.0.0.0', '[::1]'] |

## Dependencies
- nginx

## Installation
Add this role to the requirements.yml of your playbook as follows:
```yaml
roles:
  - name: ansible-proserver-mailpit
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
