# GitHub Pages deployment

This repository publishes from `main` at the repository root. The intended custom domain is
`lyncodsp.com`; `CNAME` is source-controlled so later commits cannot silently lose that binding.

## One attended Namecheap operation

In Namecheap BasicDNS/PremiumDNS/FreeDNS, remove only conflicting parking or redirect records for
`@` and `www`. Preserve every MX, TXT, SPF, DKIM, and DMARC record used by email.

Add these records with TTL Automatic:

| Type | Host | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `brookcub.github.io` |

Do not change nameservers and do not add a wildcard record. GitHub recommends verifying the apex
domain under the personal account's **Settings → Pages** and retaining the verification TXT record.

## Verification

After DNS propagation, verify:

- `lyncodsp.com` resolves to all four GitHub Pages IPv4 addresses;
- `www.lyncodsp.com` is a CNAME to `brookcub.github.io`;
- `https://lyncodsp.com/`, `/privacy/`, `/eula/`, and `/refunds/` return 200;
- the legacy `.html` paths redirect to the directory routes;
- GitHub Pages reports the custom domain configured and HTTPS enforced.

Official guidance:

- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages
- https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https
