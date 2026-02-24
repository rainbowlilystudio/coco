# Coco Protocol Specification

## Version 0.1 — February 2026

---

## Overview

Coco (Come in, this is what you Can dO) is an open protocol that enables websites to declare permissions for AI agents through a simple JSON file.

This specification defines:
- The `coco.json` file format
- Permission types and values
- Agent identification requirements
- Implementation guidelines

---

## 1. The coco.json File

### 1.1 Location

The `coco.json` file MUST be placed at the root of the website:

```
https://example.com/coco.json
```

### 1.2 Content Type

The file MUST be served with:
```
Content-Type: application/json
```

### 1.3 Encoding

The file MUST be encoded in UTF-8.

---

## 2. File Structure

### 2.1 Required Fields

```json
{
  "coco_version": "0.1",
  "site": "example.com",
  "welcome": true,
  "permissions": { }
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `coco_version` | string | Yes | Protocol version (currently "0.1") |
| `site` | string | Yes | Domain this file applies to |
| `welcome` | boolean | Yes | Whether agents are welcome at all |
| `permissions` | object | Yes | Permission declarations |

### 2.2 Optional Fields

```json
{
  "coco_version": "0.1",
  "site": "example.com",
  "welcome": true,
  "permissions": { },
  "contact": "agents@example.com",
  "human_readable": "We welcome AI agents to browse our listings...",
  "rate_limit": {
    "requests_per_minute": 60
  },
  "agent_requirements": { },
  "paths": { }
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `contact` | string | No | Contact email for agent operators |
| `human_readable` | string | No | Plain English description of policy |
| `rate_limit` | object | No | Rate limiting requirements |
| `agent_requirements` | object | No | Requirements for agents |
| `paths` | object | No | Path-specific permissions |

---

## 3. Permissions

### 3.1 Permission Categories

Permissions are organized into categories:

#### READ Permissions (Information Gathering)

| Permission | Type | Description |
|------------|------|-------------|
| `read_public` | boolean | Read publicly available content |
| `read_listings` | boolean | Read product/service/job listings |
| `read_prices` | boolean | Read pricing information |
| `read_availability` | boolean | Read availability/inventory status |
| `read_reviews` | boolean | Read user reviews and ratings |
| `read_profiles` | boolean | Read public user profiles |

#### SUBMIT Permissions (Forms & Applications)

| Permission | Type | Description |
|------------|------|-------------|
| `submit_forms` | boolean | Submit general forms |
| `submit_application` | boolean | Submit applications (jobs, schools, etc.) |
| `make_reservation` | boolean | Make reservations/bookings |
| `book_appointment` | boolean | Book appointments |
| `submit_inquiry` | boolean | Submit contact/inquiry forms |

#### ACCOUNT Permissions (User Management)

| Permission | Type | Description |
|------------|------|-------------|
| `create_account` | boolean | Create new accounts for users |
| `login_for_user` | boolean | Log in on behalf of user (with user auth) |
| `update_profile` | boolean | Update user profile information |
| `manage_preferences` | boolean | Manage user preferences/settings |

#### PURCHASE Permissions (Transactions)

| Permission | Type | Description |
|------------|------|-------------|
| `add_to_cart` | boolean | Add items to shopping cart |
| `purchase` | boolean | Complete purchases |
| `purchase_limit` | string | Maximum purchase amount (e.g., "$500") |
| `subscribe` | boolean | Create subscriptions |
| `cancel_subscription` | boolean | Cancel subscriptions |

#### CONTENT Permissions (User-Generated Content)

| Permission | Type | Description |
|------------|------|-------------|
| `post_review` | boolean | Post reviews |
| `post_comment` | boolean | Post comments |
| `upload_content` | boolean | Upload files/media |
| `send_message` | boolean | Send messages to other users |

### 3.2 Default Values

If a permission is not specified, it defaults to `false`.

If `welcome` is `false`, all permissions are implicitly `false`.

---

## 4. Agent Requirements

### 4.1 Identification Requirements

```json
{
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true,
    "must_log_actions": true
  }
}
```

| Requirement | Description |
|-------------|-------------|
| `must_identify` | Agent must identify itself in requests |
| `must_state_purpose` | Agent must state what it's trying to do |
| `must_state_user` | Agent must indicate it's acting for a user |
| `must_log_actions` | Agent must maintain action logs |

### 4.2 Agent Request Headers

Agents SHOULD include these headers when making requests:

```
Coco-Agent: AgentName/Version
Coco-Purpose: "Finding job listings for user"
Coco-User: anonymous | user_id_hash
Coco-Permissions-Requested: read_listings, submit_application
```

---

## 5. Path-Specific Permissions

Websites may specify different permissions for different paths:

```json
{
  "paths": {
    "/public/*": {
      "read_public": true
    },
    "/jobs/*": {
      "read_listings": true,
      "submit_application": true
    },
    "/checkout/*": {
      "purchase": true,
      "purchase_limit": "$1000"
    },
    "/admin/*": {
      "welcome": false
    }
  }
}
```

Path-specific permissions override root permissions.

---

## 6. Rate Limiting

```json
{
  "rate_limit": {
    "requests_per_minute": 60,
    "requests_per_hour": 1000,
    "requests_per_day": 10000,
    "concurrent_requests": 5
  }
}
```

Agents MUST respect rate limits. Exceeding limits may result in blocking.

---

## 7. Complete Example

```json
{
  "coco_version": "0.1",
  "site": "jobboard.example.com",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help users find and apply for jobs. Agents may browse all public listings, filter and search, and submit applications on behalf of authenticated users. We do not allow automated account creation or posting of job listings.",
  
  "contact": "agents@jobboard.example.com",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_prices": false,
    "submit_application": true,
    "create_account": false,
    "purchase": false,
    "post_content": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true
  },
  
  "rate_limit": {
    "requests_per_minute": 30,
    "requests_per_hour": 500
  },
  
  "paths": {
    "/api/apply/*": {
      "submit_application": true
    },
    "/admin/*": {
      "welcome": false
    }
  }
}
```

---

## 8. Implementation Guidelines

### 8.1 For Websites

1. Create a `coco.json` file
2. Place it at your domain root
3. Declare your permissions honestly
4. Monitor agent traffic
5. Update permissions as needed

### 8.2 For Agent Developers

1. Check for `coco.json` before interacting with any site
2. Respect all permissions — if it's not explicitly allowed, don't do it
3. Identify your agent in request headers
4. Respect rate limits
5. Log all actions for transparency
6. Provide users visibility into agent actions

### 8.3 For Users

1. Only authorize agents you trust
2. Review what permissions your agent requests
3. Monitor agent activity
4. Revoke access if needed

---

## 9. Relationship to Other Standards

| Standard | Relationship to Coco |
|----------|---------------------|
| **robots.txt** | Coco complements robots.txt. robots.txt blocks crawlers; Coco invites agents with permissions. |
| **MCP** | Coco defines website permissions; MCP connects agents to tools. They work together. |
| **A2A** | Coco is agent-to-website; A2A is agent-to-agent. Complementary. |
| **OAuth** | Coco declares what's allowed; OAuth handles authentication when needed. |

---

## 10. Versioning

This specification follows semantic versioning.

- **0.1** — Initial draft (February 2026)

Future versions will maintain backward compatibility where possible.

---

## 11. License

This specification is released under Creative Commons CC0 1.0 Universal (Public Domain).

Anyone may implement, extend, or build upon this specification without restriction.

---

## 12. Authors

**Rainbow Lily Studio**

February 2026

---

## 13. Contributing

This is an open standard. Contributions welcome.

- GitHub: rainbowlilystudio/coco
- Email: aya@rainbowlilystudio.com

---

*Coco: Come in, this is what yOu Can dO* 🥥
