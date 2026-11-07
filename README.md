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

## Packs (15 packs · 227 entities)

| Pack | Entities | What's inside |
|---|---|---|
| `vendor-fortigate` | 22 | FortiOS CLI — system, interfaces, policies, VPN, HA, sessions, debug-flow troubleshooting |
| `vendor-cisco-asa` | 20 | ASA CLI — NAT, ACLs, VPN, failover, **packet-tracer** |
| `vendor-f5-bigip` | 16 | BIG-IP tmsh — LTM virtuals/pools/monitors, iRules, HA, certs |
| `vendor-fortiweb` | 14 | FortiWeb — protection profiles, signatures, IP reputation, ML |
| `vendor-fortiauthenticator` | 12 | Users, RADIUS/LDAP, certificates (CA/CSR/SCEP), SSO/FIDO |
| `vendor-waf` | 16 | WAF concepts — ModSecurity, OWASP CRS paranoia levels, tuning |
| `splunk-operations` | 18 | Splunk deployment — forwarders, indexes, clustering, btool, licensing |
| `security-plus` | 24 | Security+ core, IDS/IPS **signature types** (Snort/Suricata), attack families |
| `owasp-top10` | — | covered inside `security-plus` → A01–A10, one entry per risk |
| `iso-standards` | 16 | ISO/IEC 27001 family, 22301, 15408 (Common Criteria), 27035/27033 |
| `vendor-juniper` | 10 | Junos CLI — interfaces, OSPF/BGP, commit/rollback |
| `vendor-mikrotik` | 11 | RouterOS — firewall, routes, hotspot, tools |
| `vendor-palo-alto` | 10 | PAN-OS — sessions, security policy, HA, packet-diag |
| `vendor-pfsense-opnsense` | 11 | pfctl, filter logs, easyrule, config backup |
| `vendor-checkpoint-sophos` | 11 | Check Point Gaia (cpview, fw monitor) + Sophos SSH CLI |
| `virtualization-cloud` | 16 | Proxmox, Docker, Kubernetes, AWS/Azure/GCP networking CLIs |
| `monitoring-elk-prometheus` | — | planned next release |

## Publishing a pack

See [docs/PACK-SPEC.md](https://github.com/IzumiRain/Network_PP/blob/main/docs/PACK-SPEC.md)
in the main repository. Pack content is Markdown-only data — the app renders
it, never executes it. Every pack zip is hashed; index.json carries the
SHA-256.

## License

Pack content: PolyForm Noncommercial 1.0.0 (same as the main project) unless
a pack states its own attribution.
