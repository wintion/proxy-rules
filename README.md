# Proxy Rules

Public Clash/Mihomo rules for macOS and iOS clients.

This repository should only contain public routing rules and profile templates.
Do not commit real proxy nodes, passwords, subscription tokens, or private
provider files.

## Public Subscription

After pushing this repository to GitHub, use this profile URL:

```text
https://raw.githubusercontent.com/wintion/proxy-rules/main/trojan/public.yaml
```

If the default branch is not `main`, replace `main` with the actual branch name.

The public profile references a local proxy provider:

```yaml
proxy-providers:
  personal:
    type: file
    path: ./proxy_providers/personal.yaml
```

Everyone subscribes to the same public profile, but each person keeps their own
`personal.yaml` on their device.

## Personal Nodes

Create a local file named:

```text
proxy_providers/personal.yaml
```

relative to the client's Clash/Mihomo profile directory. For Mihomo, this is
usually under the `HomeDir` used by the client. Different macOS and iOS apps
show this directory differently, so use the app's "open config folder",
"files", or "profile files" UI when available.

Use `trojan/proxy_providers/personal.example.yaml` as a starting point:

```yaml
proxies:
  - name: My-Trojan
    type: trojan
    server: example.com
    port: 443
    password: change-me
    sni: example.com
    skip-cert-verify: false
    udp: true
```

The proxy name can be anything. The public profile will load all nodes from the
`personal` provider and expose them in the `Proxy` policy group.

## Policy Groups

The public profile keeps policy groups intentionally simple:

| Group | Purpose |
| --- | --- |
| `Auto` | Automatically selects the fastest personal node. |
| `Proxy` | Main proxy switch. Choose `Auto`, `DIRECT`, or a specific personal node. |
| `Final` | Fallback for traffic that does not match earlier rules. |

## Rule Maintenance

Most daily rule changes should happen under `trojan/rules/`, not in
`trojan/public.yaml`.

| File | Target group | Use for |
| --- | --- | --- |
| `trojan/rules/custom-direct.yaml` | `DIRECT` | Sites that should always bypass the proxy. |
| `trojan/rules/custom-proxy.yaml` | `Proxy` | Sites that should use the proxy. |

Each file is a domain rule-provider file:

```yaml
payload:
  - '+.example.com'
  - 'exact.example.com'
```

Use `+.example.com` when both the root domain and subdomains should match. Use
`exact.example.com` only when the exact host should match.

Only edit `trojan/public.yaml` when changing DNS, policy groups, provider URLs,
or the top-level rule order.

Rules are matched from top to bottom. The public profile applies custom rules
before large upstream rule sets, so your own rules can override the defaults.

## Local Private Files

These files are intentionally ignored by Git:

```text
trojan/pc.yaml
trojan/ios.yaml
trojan/*.local.yaml
trojan/*.private.yaml
trojan/proxy_providers/*.yaml
```

Keep your current working config in `trojan/pc.yaml` if you want. It will not be
committed unless forced manually.

## Validation

Basic YAML validation:

```sh
ruby -e 'require "yaml"; YAML.load_file("trojan/public.yaml"); puts "YAML OK"'
```

Full profile validation should be done with the actual Clash/Mihomo client you
use, because iOS and macOS clients differ in how they resolve local provider
paths.
