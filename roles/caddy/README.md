# Caddy

## Webserver/Reverse Proxy

### Dependencies

* None

### Variables

| Variable                 | Description                 | Default                |
| ------------------------ | --------------------------- | ---------------------- |
| `email`                  | email for letsencrypt       | `none`                 |
| `caddy_config_location`  | caddy config file location  | `/etc/caddy/Caddyfile` |
| `deploy_example_service` | deploy the hello world page | `true`                 |
| `caddy_acme_ca`          | ACME endpoint               | `none`                 |

### Notes

Configuration is done with `blockinfile` instead of `template` because it allows
other roles to define services + chunks to pass directly to `add_service`, and
so it'd be good to keep the modules used in this role consistent. Plus, it comes
with the added benefit that we'll be later able to update blocks directly.

Included is an example service for caddy (`tasks/example_service.yml`), but you
can disable that by setting `deploy_example_service` to `false`.

Caddy configuration is validated every time as part of the task!

If a custom ACME CA is provided `caddy_acme_ca`, it will be used.
