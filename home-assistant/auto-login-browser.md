# Auto login in Home assistant

in configuration.yaml

```
homeassistant:
  auth_providers:
    - type: trusted_networks
      trusted_networks:
        - 192.168.178.103
        - ...
      trusted_users:
        192.168.178.103: 12345678901234
        ...
      allow_bypass_login: true
    - type: homeassistant
```

*note*: the id in the mapping list trusted_users is the id generated by Home Assistant, and has nothing to do with user name

- restart HA