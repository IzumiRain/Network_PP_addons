# Model documents (v2 draft, dev branch)

> Status: **draft on `dev/data-driven-model-docs`**. As of Slice 2, all 15
> packs in `packs/` + `index.json` are rebuilt at **1.2.0** from v2 model
> documents (24 document entities; coverage of the old per-command files
> was verified title-by-title before their removal — git history keeps
> them). This document mirrors "Document model (v2 draft)" in the main
> repo's `docs/PACK-SPEC.md` — if the two disagree, PACK-SPEC wins.

## One Markdown document per Model/id

In v1 a pack holds many small files — one per command. In v2, a vendor
model gets **one** Markdown document containing *all* of its documentation:

```
F5 BIG-IP 4000  →  one .md   (System, LTM, Pools/Monitors, Connections,
                              HA, Certificates, iRules, Logs, NAT…)
```

Frontmatter (same fields as v1, new conventions):

| Field | v2 rule |
|---|---|
| `id` | ends with the model/id slug — e.g. `doc/f5/bigip/4000` |
| `kind` | `vendor` for model documents (`runbook` for runbook documents) |
| `title` | e.g. `F5 BIG-IP 4000` |
| `category` | `reference/vendors/<company>/<product>/<model>` — e.g. `reference/vendors/f5/bigip/4000` |
| `tags` | document-level tags only; topics are tagged per section |
| `version` | vendor applicability — e.g. `BIG-IP 16.1 / 17.x` |

## Section tags

Every `##` heading in the body is a **section**, and each section carries
its own tags via an HTML-comment marker directly under the heading:

```markdown
## LTM — pools and monitors
<!-- section-tags: ltm, pools, monitors -->
```

The marker is invisible when rendered and is parsed (and stripped) by the
app: sections are exposed as `entity.sections: [{ title, tags, body }]`.
Content before the first `##` is the preamble section (empty title).
`###`+ headings are ordinary content inside a section.

## Generic category parsing — no hardcoded lists

Categories are slug paths and the app derives all structure from them
positionally (Rust `parse_category_path`, command `content_category_path`):

```
reference/vendors/<company>/<product>/<model>[/<topic>…]
    root / category / company   / device  / model [/ topic…]
reference/<area>[/<group>[/<topic>…]]     → root / category / group [/ topic…]
runbooks/<area>[/<topic>…]                → root / area [/ topic…]
```

No vendor, product or section name is hardcoded anywhere: uploading a pack
for a brand-new company here makes it appear in the app's tree
(Category → Company → Device → Model/id) with no app release. Only the
deepest Model/id level opens a document; upper levels are navigation.

## How users get content

Unchanged from v1: packs are published here as `packs/*.zip` + `index.json`
(SHA-256 verified by the app), and users download only the packs they want.
The v2 zip rebuild happens in a later slice, after the app-side parser ships.

## Pilot

- Main repo, `addons-src/vendor-f5-bigip/content/bigip-4000.md` — the F5
  BIG-IP pack merged into one model document (original per-command files
  kept during migration; see that pack's README).
- Main repo, `addons-src/vendor-fortigate/content/fortigate-runbook-policy.md`
  — a pilot v2 runbook document from the existing FortiGate runbook.
