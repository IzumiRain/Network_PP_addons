# Network++ Addons Registry

Content-pack registry for [Network++](https://github.com/IzumiRain/Network_PP).

`index.json` lists every published pack: id, version, description, size,
**SHA-256** and download URL. The app verifies the checksum before installing.

## Using this registry

Settings → Content packs → set the registry URL to one of:

- `https://raw.githubusercontent.com/IzumiRain/Network_PP_addons/main/index.json`
- jsDelivr mirror (works from networks where raw GitHub is blocked):
  `https://cdn.jsdelivr.net/gh/IzumiRain/Network_PP_addons@main/index.json`

Optional: Settings → Content packs → proxy (`socks5://host:port` or
`http://host:port`) for restricted networks. You can also install any pack
zip directly from a file — no registry needed.

## Packs

| Pack | What's inside |
|---|---|
| `vendor-fortigate` | FortiOS CLI — system, interfaces, policies, VPN, HA, sessions, troubleshooting |
| `vendor-fortiweb` | FortiWeb WAF — policies, signatures, IP reputation, ML protection |
| `vendor-fortiauthenticator` | FortiAuthenticator — users, certificates, RADIUS/LDAP, SSO |
| `vendor-cisco-asa` | Cisco Secure Firewall (ASA) CLI — NAT, ACLs, VPN, failover, packet-tracer |
| `vendor-f5-bigip` | F5 BIG-IP tmsh — LTM virtuals/pools/monitors, iRules, HA, certs |
| `vendor-waf` | WAF concepts — ModSecurity, OWASP CRS, positive security, tuning |
| `splunk-operations` | Splunk deployment & troubleshooting — forwarders, indexes, clustering, btool |
| `security-plus` | Security+ core, signature & detection types, attack families |
| `owasp-top10` | OWASP Top 10 (2021) — one entry per risk with defenses |
| `iso-standards` | ISO/IEC standards — 27001/27002/27005/27017/27018/27701/22301/15408 |
| `vendor-juniper` | Junos CLI essentials |
| `vendor-mikrotik` | RouterOS CLI essentials |
| `vendor-palo-alto` | PAN-OS CLI essentials |
| `vendor-pfsense-opnsense` | pfSense/OPNsense — pfctl, logs, config |
| `vendor-checkpoint-sophos` | Check Point Gaia + Sophos Firewall |
| `virtualization-cloud` | Proxmox, Docker, Kubernetes, AWS/Azure/GCP networking CLIs |
| `monitoring-elk-prometheus` | ELK stack, Prometheus, Grafana, Zabbix |

## Publishing a pack

See [docs/PACK-SPEC.md](https://github.com/IzumiRain/Network_PP/blob/main/docs/PACK-SPEC.md)
in the main repository. Pack content is Markdown-only data — the app renders
it, never executes it. Every pack zip is hashed; index.json carries the
SHA-256.

## License

Pack content: PolyForm Noncommercial 1.0.0 (same as the main project) unless
a pack states its own attribution.
