# Custom Domain Configuration for AgentRules.dev

## Option A: Dedicated Domain (agentrules.dev)
Add these DNS records at your domain registrar / Cloudflare:

| Type | Name | Content | Proxy status |
| :--- | :--- | :--- | :--- |
| A | @ | 185.199.108.153 | DNS only (or Proxied) |
| A | @ | 185.199.109.153 | DNS only (or Proxied) |
| A | @ | 185.199.110.153 | DNS only (or Proxied) |
| A | @ | 185.199.111.153 | DNS only (or Proxied) |
| CNAME | www | ceopatinhalo-ai.github.io | DNS only (or Proxied) |

Then run:
```bash
echo "agentrules.dev" > CNAME
git add CNAME DNS_SETUP.md
git commit -m "feat: configure custom domain agentrules.dev"
git push origin main
```

## Option B: Subdomain of tema.vn (agentrules.tema.vn)
If you want to host it under your existing domain `tema.vn`:

| Type | Name | Content | Proxy status |
| :--- | :--- | :--- | :--- |
| CNAME | agentrules | ceopatinhalo-ai.github.io | DNS only |

Then set CNAME to `agentrules.tema.vn`.
