# ansible-composer

Setups ElasticSearch.

### Example playbook
```yaml
---
- hosts: myserver
  roles:
    - role: sunfoxcz.elasticsearch
      elasticsearch_version: 7.x # optional
      elasticsearch_jvm_options:
        - Xms2g
        - Xmx2g
```

## License

Licensed under MIT license. See [LICENSE](LICENSE.md) for details.
