# Trellis New Relic infrastructure monitoring

Install [New Relic infrastructure monitoring](https://docs.newrelic.com/docs/infrastructure/infrastructure-monitoring/get-started/get-started-infrastructure-monitoring/) on [Trellis](https://github.com/roots/trellis) servers.

## Requirements

- [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html) v2.7 or later
- Python v3.7.6 or later
- [Trellis](https://github.com/roots/trellis) v1.3.0 or later
- [New Relic](https://newrelic.com/) account

## Installation

Add these secrets to `group_vars/<environment>/vault.yml`:

```yaml
# Documentation: https://github.com/resenseagency/trellis-newrelic-infra
vault_newrelic_api_key: xxxx-xxxxxxxxxxxxxxxxxxxxxxxxxxx
vault_newrelic_account_id: xxxxxxx
vault_newrelic_region: xx
```

Add this role to `galaxy.yml`:

```yaml
- name: trellis-newrelic-infra
  src: https://github.com/resenseagency/trellis-newrelic-infra
  type: git
```

Add this role to `dev.yml` and `server.yml`:

```diff
  # `dev.yml` & `server.yml`

  roles:
      # Some other Trellis roles ...
+     - { role: trellis-newrelic-infra, tags: [newrelic-infra] }
```

Run `$ trellis galaxy install` to install this new role.
