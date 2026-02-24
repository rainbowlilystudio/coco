# Coco Example Files

## Example coco.json Files for Different Website Types

---

## 1. E-Commerce (Shopping Site)

**amazon-style.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "shop.example.com",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help users shop. Agents may browse products, compare prices, add to cart, and complete purchases on behalf of authenticated users.",
  
  "contact": "agent-support@shop.example.com",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_prices": true,
    "read_availability": true,
    "read_reviews": true,
    "add_to_cart": true,
    "purchase": true,
    "purchase_limit": "$500",
    "create_account": false,
    "post_review": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_user": true
  },
  
  "rate_limit": {
    "requests_per_minute": 60
  }
}
```

---

## 2. Restaurant Reservations

**opentable-style.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "reservations.example.com",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help users discover restaurants and make reservations. Agents may search, view availability, and book tables on behalf of users.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_availability": true,
    "read_reviews": true,
    "make_reservation": true,
    "submit_inquiry": true,
    "create_account": false,
    "post_review": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true
  },
  
  "rate_limit": {
    "requests_per_minute": 30
  }
}
```

---

## 3. Job Board

**indeed-style.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "jobs.example.com",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help job seekers find opportunities. Agents may search listings, filter by criteria, and submit applications on behalf of authenticated users.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "submit_application": true,
    "upload_content": true,
    "create_account": false,
    "post_content": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true,
    "must_log_actions": true
  },
  
  "rate_limit": {
    "requests_per_minute": 20,
    "requests_per_hour": 200
  },
  
  "paths": {
    "/apply/*": {
      "submit_application": true,
      "upload_content": true
    },
    "/post-job/*": {
      "welcome": false
    }
  }
}
```

---

## 4. Auditions & Casting

**auditions.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "auditions.example.com",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help performers find audition opportunities. Agents may browse castings, filter by type/location, and submit applications with portfolios on behalf of users.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_availability": true,
    "submit_application": true,
    "upload_content": true,
    "create_account": false,
    "post_content": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true
  },
  
  "rate_limit": {
    "requests_per_minute": 30
  }
}
```

---

## 5. News Site (Restrictive)

**news-site.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "news.example.com",
  "welcome": true,
  
  "human_readable": "We allow AI agents to read headlines and summaries only. Full article content is for subscribers. Agents may help users subscribe.",
  
  "permissions": {
    "read_public": true,
    "read_listings": false,
    "subscribe": true,
    "purchase": false,
    "post_comment": false
  },
  
  "paths": {
    "/headlines/*": {
      "read_public": true
    },
    "/full-article/*": {
      "read_public": false
    },
    "/subscribe/*": {
      "subscribe": true
    }
  },
  
  "rate_limit": {
    "requests_per_minute": 10
  }
}
```

---

## 6. Healthcare / Appointments

**healthcare.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "health.example.com",
  "welcome": true,
  
  "human_readable": "We allow AI agents to help patients find providers and book appointments. Patient data requires authentication. Agents may not access medical records.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_availability": true,
    "book_appointment": true,
    "submit_inquiry": true,
    "read_profiles": false,
    "create_account": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true,
    "must_log_actions": true
  },
  
  "paths": {
    "/patient-portal/*": {
      "welcome": false
    },
    "/find-doctor/*": {
      "read_listings": true,
      "read_availability": true
    }
  },
  
  "rate_limit": {
    "requests_per_minute": 20
  }
}
```

---

## 7. Travel Booking

**travel.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "travel.example.com",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help users plan and book travel. Agents may search flights, hotels, and activities, compare prices, and complete bookings.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_prices": true,
    "read_availability": true,
    "read_reviews": true,
    "make_reservation": true,
    "purchase": true,
    "purchase_limit": "$5000",
    "create_account": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_user": true
  },
  
  "rate_limit": {
    "requests_per_minute": 60,
    "concurrent_requests": 5
  }
}
```

---

## 8. Government / Public Services

**government.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "services.gov.example",
  "welcome": true,
  
  "human_readable": "We welcome AI agents to help citizens access public services. Agents may browse information, download forms, and submit applications on behalf of authenticated users.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "submit_forms": true,
    "submit_application": true,
    "upload_content": true,
    "create_account": false,
    "purchase": false
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_state_purpose": true,
    "must_state_user": true,
    "must_log_actions": true
  },
  
  "rate_limit": {
    "requests_per_minute": 30
  }
}
```

---

## 9. Closed Site (No Agents)

**private-site.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "private.example.com",
  "welcome": false,
  
  "human_readable": "This site does not permit AI agent access. Please use our website directly.",
  
  "contact": "support@private.example.com"
}
```

---

## 10. Bank / Financial Services (Highly Restricted)

**bank.coco.json**

```json
{
  "coco_version": "0.1",
  "site": "bank.example.com",
  "welcome": true,
  
  "human_readable": "We allow limited AI agent access for information only. Agents may read public information about our services. All transactions require direct user authentication through our secure portal.",
  
  "permissions": {
    "read_public": true,
    "read_listings": true,
    "read_prices": true,
    "submit_forms": false,
    "create_account": false,
    "purchase": false,
    "login_for_user": false
  },
  
  "paths": {
    "/products/*": {
      "read_public": true,
      "read_listings": true
    },
    "/online-banking/*": {
      "welcome": false
    },
    "/account/*": {
      "welcome": false
    }
  },
  
  "agent_requirements": {
    "must_identify": true,
    "must_log_actions": true
  },
  
  "rate_limit": {
    "requests_per_minute": 10
  }
}
```

---

## Usage Notes

### For Website Owners:

1. Copy the example closest to your site type
2. Modify permissions to match your policy
3. Save as `coco.json` in your website root
4. Test by accessing `https://yoursite.com/coco.json`

### For Agent Developers:

1. Always check for `coco.json` first
2. Parse permissions before taking action
3. Respect all limitations
4. Identify your agent in headers

---

*Coco: Come in, this is what yOu Can dO* 🥥
