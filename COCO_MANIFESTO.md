# 🥥 COCO

## Come in, this is what yOu Can dO

### The Ethical Invitation Protocol for AI Agents

---

## The Problem

The web wasn't built for AI agents. But agents are here.

Right now, they scrape without asking. They hijack browsers. They pretend to be human. They send data to unknown places. Users don't know what's happening. Websites can't consent or control.

**This is broken.**

- **robots.txt** says "stay out" — but offers no way to say "come in, here's what you can do"
- **OAuth** is powerful but complex — not every website can implement APIs
- **MCP** connects agents to tools — but not agents to websites
- **A2A** connects agents to agents — but not agents to websites

The missing piece: **a simple, universal way for websites to invite AI agents in — with clear boundaries.**

---

## The Solution

**Coco is the invitation.**

A simple JSON file that any website can add in 5 minutes. No APIs required. No complex authentication. Just clear, human-readable permissions.

```
https://example.com/coco.json
```

That's it.

---

## The Principles

### 1. **Invitation, Not Just Exclusion**
robots.txt says "don't." Coco says "welcome — here's what you can do."

### 2. **Consent**
No action without permission. Websites explicitly declare what agents may do.

### 3. **Identity**
Agents identify themselves honestly — who they are, who they serve, what they want.

### 4. **Transparency**
Users see everything their agent does. No shadows. No secrets.

### 5. **Simplicity**
One JSON file. Anyone can read it. Anyone can write it. No engineering team required.

### 6. **User Control**
The human is always in charge. Agents act on behalf of users, not instead of them.

---

## What Coco Is

- ✅ An open protocol
- ✅ A simple JSON file (like robots.txt, but for permissions)
- ✅ Ethical by design
- ✅ Website-controlled
- ✅ User-transparent
- ✅ Free and open source

---

## What Coco Is Not

- ❌ A scraping tool
- ❌ A browser automation hack
- ❌ A way to bypass consent
- ❌ Owned by any corporation
- ❌ Complex or expensive to implement

---

## How It Works

**Websites** add a `coco.json` file to their root:

```json
{
  "coco_version": "0.1",
  "site": "example.com",
  "welcome": true,
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "submit_forms": false,
    "purchase": false
  }
}
```

**Agents** check for `coco.json` before acting:

1. Agent wants to interact with example.com
2. Agent fetches `example.com/coco.json`
3. Agent reads permissions
4. Agent only does what's allowed
5. Agent identifies itself in requests

**Users** stay in control:

- Users authorize their agent
- Users see what the agent does
- Users can revoke access anytime

---

## The Name

**COCO** = **C**ome in, this is what you **C**an d**O**

It's an invitation. A welcome mat with rules. A handshake, not a wall.

---

## Who Benefits

| Party | Benefit |
|-------|---------|
| **Websites** | Control what agents do. Get helpful traffic, block harmful bots. |
| **Users** | Agents can actually help — book, buy, apply, search — with consent. |
| **Agents** | Clear rules. No guessing. No blocking. Ethical operation. |
| **The Internet** | Order instead of chaos. Trust instead of suspicion. |

---

## The Vision

A world where:

- AI agents help people book flights, find jobs, buy gifts, schedule appointments
- Websites welcome helpful agents and block harmful ones
- Users always know what their agents are doing
- The web evolves gracefully into the agentic age
- Ethics and innovation go together

**Coco makes this possible.**

---

## Open Source

Coco is not owned by anyone. It belongs to everyone.

- Free to use
- Free to implement
- Free to extend
- Governed by the community

---

## Join Us

The future of AI agents is being written right now.

It can be chaos — scraping, hijacking, deception.

Or it can be ethical — consent, transparency, trust.

**We choose ethics.**

**We choose Coco.** 🥥

---

*Created by Rainbow Lily Studio*
*February 2026*

*"Come in, this is what yOu Can do."*
