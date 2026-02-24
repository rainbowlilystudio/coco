# 🥥 Coco Protocol

### Come in, this is what yOu Can dO

**The ethical invitation protocol for AI agents to interact with websites.**

---

## What is Coco?

Coco is a simple, open standard that allows websites to declare what AI agents can and cannot do — through a single JSON file.

Like `robots.txt` told search engines where not to go, `coco.json` tells AI agents what they're **welcome** to do.

---

## Quick Start

### For Website Owners

Add a `coco.json` file to your website root:

```json
{
  "coco_version": "0.1",
  "site": "yoursite.com",
  "welcome": true,
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "submit_forms": false,
    "purchase": false
  }
}
```

That's it. Agents will check `https://yoursite.com/coco.json` before interacting.

### For Agent Developers

Before interacting with any website:

1. Fetch `https://site.com/coco.json`
2. Check if `welcome` is `true`
3. Only perform actions that are permitted
4. Identify your agent in request headers

---

## Documentation

| Document | Description |
|----------|-------------|
| [COCO_MANIFESTO.md](./COCO_MANIFESTO.md) | The vision and principles |
| [COCO_SPEC_v0.1.md](./COCO_SPEC_v0.1.md) | Technical specification |
| [COCO_EXAMPLES.md](./COCO_EXAMPLES.md) | Example files for different site types |
| [coco.json](./coco.json) | Template file |

---

## The Problem

AI agents are everywhere — shopping, booking, applying, searching. But there's no standard way for websites to say what agents can do.

- **robots.txt** only says "don't crawl"
- **OAuth** is complex and requires APIs
- **MCP** connects agents to tools, not websites
- **Scraping** is chaotic and unethical

**Coco fills the gap.**

---

## The Solution

One JSON file. Clear permissions. Ethical by design.

```
https://yoursite.com/coco.json
```

Websites declare permissions. Agents respect them. Users stay in control.

---

## Principles

1. **Invitation, Not Exclusion** — "Welcome, here's what you can do"
2. **Consent** — No action without permission
3. **Identity** — Agents identify themselves honestly
4. **Transparency** — Users see what agents do
5. **Simplicity** — One file, anyone can implement

---

## Permission Types

| Category | Examples |
|----------|----------|
| **Read** | `read_public`, `read_listings`, `read_prices` |
| **Submit** | `submit_forms`, `make_reservation`, `book_appointment` |
| **Account** | `create_account`, `login_for_user` |
| **Purchase** | `add_to_cart`, `purchase`, `purchase_limit` |
| **Content** | `post_review`, `upload_content` |

See [COCO_SPEC_v0.1.md](./COCO_SPEC_v0.1.md) for full details.

---

## Examples

- [E-commerce site](./COCO_EXAMPLES.md#1-e-commerce-shopping-site)
- [Restaurant reservations](./COCO_EXAMPLES.md#2-restaurant-reservations)
- [Job board](./COCO_EXAMPLES.md#3-job-board)
- [Healthcare](./COCO_EXAMPLES.md#6-healthcare--appointments)
- [News site](./COCO_EXAMPLES.md#5-news-site-restrictive)
- [Bank (restricted)](./COCO_EXAMPLES.md#10-bank--financial-services-highly-restricted)

---

## Why "Coco"?

**C**ome in, this is what you **C**an d**O**

It's an invitation. A welcome mat with rules. A handshake, not a wall. 🥥

---

## Relationship to Other Standards

| Standard | Coco's Role |
|----------|-------------|
| robots.txt | Coco complements it — robots.txt blocks, Coco invites |
| MCP | Coco is agent-to-website; MCP is agent-to-tool |
| A2A | Coco is agent-to-website; A2A is agent-to-agent |
| OAuth | Coco declares permissions; OAuth handles auth |

---

## License

**CC0 1.0 Universal (Public Domain)**

This is an open standard. Use it freely. Build on it. Make it better.

---

## Created By

**Rainbow Lily Studio**


February 2026

---

## Contributing

This is an open standard. We welcome:

- Feedback on the spec
- Example implementations
- Translations
- Use cases

Open an issue or submit a PR.

---

*"Come in, this is what yOu Can dO."* 🥥
