# ansible-elasticsearch

Setups ElasticSearch.

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

## License

Licensed under MIT license. See [LICENSE](LICENSE.md) for details.
