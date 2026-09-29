# Cookery Trove public website

Static website for [cookerytrove.com](https://cookerytrove.com), deployed with GitHub Pages. This repository intentionally contains only public website files and approved brand/screenshots—no app source, keys, credentials, or runtime configuration.

## Edit and preview

Edit `index.html` and `styles.css`. Keep images in `assets/`. Preview locally from the repository root:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`. No build step or package installation is required.

When the App Store listing is live, replace the coming-soon status in `index.html` with the canonical `https://apps.apple.com/...` URL and test it before publishing.

## Deploy

GitHub Pages deploys from `main` and the repository root:

1. Commit and push the static files to `main`.
2. In **Settings → Pages**, set **Source** to **Deploy from a branch**, with `main` and `/ (root)`.
3. In **Settings → Pages → Custom domain**, enter `cookerytrove.com`. The committed `CNAME` file must contain the same hostname.
4. Configure the apex DNS records listed below at the domain provider. Configure `www` as a CNAME so GitHub can redirect it to the apex domain.
5. After GitHub completes its DNS check and provisions the certificate, enable **Enforce HTTPS**.

### DNS records

| Type | Host/name | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |
| CNAME | `www` | `seachellemz.github.io` |

Remove any conflicting `A`, `AAAA`, or `CNAME` records for the same host before adding these. Do not use wildcard DNS records for the domain. DNS changes can take up to 24 hours to propagate.

Official references: [Managing a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) and [Securing Pages with HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https).

## Release check

- Test the home page at desktop and mobile widths.
- Check keyboard focus, navigation anchors, screenshots, Support, Privacy, and Contact.
- Confirm the App Store control still says coming soon or points to the live listing.
- Confirm both `https://cookerytrove.com` and `https://www.cookerytrove.com` resolve without certificate warnings.
