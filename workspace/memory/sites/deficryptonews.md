# Defi Crypto News

## Role

`deficryptonews.co` is a WordPress-based editorial site focused on crypto and Web3 news, commentary, and analysis.

## Platform

- CMS: WordPress
- REST root: `https://deficryptonews.co/wp-json/`
- Main content namespace: `wp/v2`
- Other exposed namespaces seen during testing:
- `oembed/1.0`
- `yoast/v1`
- `wp-site-health/v1`
- `wp-block-editor/v1`
- `wp-abilities/v1`

## Access Pattern

### Public Read Access

Anonymous REST reads are available.

Confirmed working:
- `GET https://deficryptonews.co/wp-json/`
- `GET https://deficryptonews.co/wp-json/wp/v2/posts`
- `GET https://deficryptonews.co/wp-json/wp/v2/posts/<id>`

### Authenticated Write Access

This site accepts WordPress Application Password authentication over Basic Auth.

Confirmed working on 2026-03-19:
- `GET /wp-json/wp/v2/users/me` with Application Password returned `200 OK`
- `POST /wp-json/wp/v2/posts/207` succeeded and updated the live post title

## Credentials For This Task

### WordPress User

- Username: `CEO`
- Display result from REST test: user `id=2`, slug `ceo`, name `Ben Rogers`

### WordPress Login Password

- Login password: `B@t3qbgPLfSKi*ixf()q5JwZ`

### WordPress Application Password

- Application Password: `dJyg Glhg D5rK qICf R0VJ BtBc`

## Verified Commands

### Verify Auth

```bash
curl -i -u 'CEO:dJyg Glhg D5rK qICf R0VJ BtBc' \
  'https://deficryptonews.co/wp-json/wp/v2/users/me'
```

Expected result:
- `200 OK`

### Read A Post

```bash
curl -sS -u 'CEO:dJyg Glhg D5rK qICf R0VJ BtBc' \
  'https://deficryptonews.co/wp-json/wp/v2/posts/207?_fields=id,slug,title,modified'
```

### Update A Post Title

```bash
curl -sS -u 'CEO:dJyg Glhg D5rK qICf R0VJ BtBc' \
  -X POST 'https://deficryptonews.co/wp-json/wp/v2/posts/207' \
  -H 'Content-Type: application/json' \
  --data '{"title":"The Kaia Conundrum: Can a Unified Giant Actually Solve the Web3 Onboarding Crisis?"}'
```

## Known Working Test Result

A live authenticated edit was completed on 2026-03-19.

- Post ID: `207`
- Post slug: `kaia-conundrum-can-a-merged-giant-actually-solve-the-web3-onboarding-crisis`
- Title before test:
- `The Kaia Conundrum: Can a Merged Giant Actually Solve the Web3 Onboarding Crisis?`
- Title after test:
- `The Kaia Conundrum: Can a Unified Giant Actually Solve the Web3 Onboarding Crisis?`

Note:
- The slug did not change after the title update, which is normal WordPress behavior.

## Operational Notes

- Normal wp-admin login password did not authenticate against REST Basic Auth.
- The WordPress Application Password did authenticate correctly.
- `Authorization` headers are reaching WordPress correctly for this route.
- No extra Apache, Nginx, or Cloudflare fix appears necessary for Application Password REST access on this site.
- Auth-only routes such as `GET /wp-json/wp/v2/users/me` return `401` when called without valid credentials.

## Recommended Workflow

1. Verify credentials with `/wp-json/wp/v2/users/me`.
2. Read the target post first and store current title/content before changing anything.
3. Make the smallest possible edit.
4. Read the post back immediately to confirm the update landed.
5. If the change is only for testing, revert it in the same session.

## Caution

- This file contains live credentials.
- Do not copy these credentials into public repos, logs, screenshots, or article content.
- Prefer rotating the Application Password after any broad sharing or testing session.
