# ansible-elasticsearch

Installs and configures Elasticsearch on Debian/Ubuntu using systemd.
Requires Ansible Core 2.15 or newer and root privileges on the managed host.

### Example playbook
```yaml
---
- hosts: myserver
  roles:
    - role: sunfoxcz.elasticsearch
      elasticsearch_version: 8.x # 8.x is default
      elasticsearch_jvm_options: # optional
        Xms: Xms2g
        Xmx: Xmx2g
```

The role uses a deb822 APT source with a repository-specific signing key. Existing
`elasticsearch.list` files created by earlier versions of this role are migrated.
`elasticsearch_version` selects the repository series; existing packages are not
automatically upgraded.

JVM overrides are written to `/etc/elasticsearch/jvm.options.d/ansible.options`.
Matching overrides from earlier versions of this role are removed from the main
`jvm.options` file. Set `elasticsearch_jvm_options: {}` to remove the managed file.

Security is disabled by default and HTTP binds to `127.0.0.1`. Change
`elasticsearch_http_host` to allow remote HTTP connections. The security settings
are controlled independently by these boolean variables (all default to `false`):

- `elasticsearch_security_enabled`
- `elasticsearch_security_enrollment_enabled`
- `elasticsearch_security_http_ssl_enabled`
- `elasticsearch_security_transport_ssl_enabled`

Existing certificate settings are preserved. Enabling SSL requires valid
certificates and, where applicable, the corresponding Elasticsearch keystore
settings. Configuration is applied before the service starts.

## License

Licensed under MIT license. See [LICENSE](LICENSE.md) for details.
