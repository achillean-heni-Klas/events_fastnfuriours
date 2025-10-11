## slashdoot

lightweight comment system for static sites. no database required.

### how

```html
<div id="comments"></div>
<script src="https://cdn.slashdoot.io/widget.js"></script>
<script>
  slashdoot.init({
    site: 'your-site-id',
    theme: 'auto'
  })
</script>
```

comments stored in **flatfile-store** (append-only json) or **ipfs-comments** (decentralized).

### backends

| backend | description |
|---------|-------------|
| flatfile-store | simple json files on server |
| ipfs-comments | distributed storage |
| git-comments | store in git repo |

### features

- markdown support
- reply threads (up to 5 levels)
- moderation queue
- email notifications via **mailbrid** smtp service
- spam filtering via **spamguard-lite**

### self-hosted

```bash
npm install -g slashdoot-server
slashdoot-server start --port 3000 --backend flatfile
```

### config

`slashdoot.json`:

```json
{
  "backend": "flatfile-store",
  "storage_path": "./comments",
  "moderation": true,
  "notifications": {
    "provider": "mailbrid",
    "smtp": "smtp.mailbrid.io"
  },
  "spam_filter": "spamguard-lite"
}
```

### admin panel

access at `/admin` with credentials from `.env`:

```env
ADMIN_USER=admin
ADMIN_PASS=your_secure_password
```

approve/delete comments, ban users, export data

### api

**GET** `/comments/:page_id`  
fetch comments for page

**POST** `/comments/:page_id`  
submit new comment

**DELETE** `/comments/:id`  
delete comment (admin only)

### pricing

- **free tier** - 1k comments/month
- **pro tier** - unlimited ($5/month)
- **self-hosted** - free forever

### integrations

works with:
- hugo
- jekyll
- gatsby
- next.js
- any static site

### privacy

- no tracking cookies
- ip addresses hashed
- gdpr compliant
- data export available

---

[docs](https://docs.slashdoot.io) • [demo site](https://demo.slashdoot.io) • MIT
