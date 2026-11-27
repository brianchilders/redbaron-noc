# redbaron-noc

The Network Operations Center (NOC) page for **redbaron enterprises**, served at
<https://www.redbaron.net/> by GitHub Pages.

It is hosted **off-net** on purpose: the page and its contact details have to
stay reachable when the redbaron network is down. Don't move it onto our own
/24 or the VPS.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole page. Inline CSS, no JavaScript, no build step. |
| `geofeed.csv` | IP geolocation feed ([RFC 8805](https://www.rfc-editor.org/rfc/rfc8805)), referenced from ARIN ([RFC 9632](https://www.rfc-editor.org/rfc/rfc9632)). |
| `CNAME` | Custom domain for GitHub Pages (`www.redbaron.net`). |
| `.nojekyll` | Turns off Jekyll so that `.well-known/` gets published. |
| `.well-known/security.txt` | Security contact file ([RFC 9116](https://www.rfc-editor.org/rfc/rfc9116)). |

To change the site, edit the files and push to `main`. Pages redeploys within a minute or two.

## Placeholders still to fill in

Anything not yet final is tagged on the page with an amber **PLACEHOLDER**
or **PLANNED** tag. To find them all, search `index.html` for `class="ph"`.
Remove the "This page is being completed" banner once they're all gone.

- [x] **Role addresses:** `noc@`, `abuse@`, `security@`, `hostmaster@` and `postmaster@` exist
      as Google Groups (abuse/postmaster can't be aliases, since Google reserves them). A Gmail
      filter keeps them out of Spam. All five are live on the page.
- [x] **ARIN role POCs:** REN32-ARIN (redbaron enterprises NOC, noc@) and REA38-ARIN
      (redbaron enterprises Abuse, abuse@) created 2026-11-26 and shown on the page.
- [ ] **Attach them to org BCSP-6:** Tech + NOC = REN32-ARIN, Abuse = REA38-ARIN, Admin = BC117-ARIN.
      Once BCSP-6 shows up in public Whois, link it on the page too.
- [x] **security.txt:** `security@` is the first Contact line.
- [ ] **ASN, IPv4 and IPv6 prefixes:** fill these in and link each to its ARIN RDAP record.
      Add bgp.tools / bgp.he.net links once the ASN is known.
- [ ] **Upstream transit:** Vultr (AS20473), Chicago, is listed with a PLANNED tag. Remove the tag
      once the BGP session is up. If a second upstream is added, list it and revisit Peering and BCP 84.
- [ ] **PeeringDB:** create the entry, link it, and set its Policy URL to `https://www.redbaron.net/#routing`.
- [ ] **RPKI:** create ROAs in ARIN Hosted RPKI. Let ARIN's IRR Auto-Manager create the route objects.
- [ ] **ROV and BCP 38:** turn on dropping of RPKI-invalid routes and source-address
      filtering on the router. Remove those tags only once they're actually done.
- [ ] **Geofeed:** uncomment the lines in `geofeed.csv` with the real prefixes, then add
      `Geofeed https://www.redbaron.net/geofeed.csv` to the ARIN NetRange comment.

## Maintenance checklist

- **Every year:** update the `Expires:` date in `.well-known/security.txt`.
  It's currently `2027-11-25`. RFC 9116 says to keep it less than a year out,
  so set a reminder for early November.
- **Keep contacts in sync with ARIN.** Every address on the page must match the ARIN
  POC records (BC117-ARIN, REN32-ARIN and REA38-ARIN).
  If you change one, change the other. ARIN sends an annual POC validation email, so answer it.
- **Keep `geofeed.csv` in sync with the Network section** whenever prefixes are added or move.
- **When you review the page**, update the "Last reviewed" date in the footer.
- **Footer:** bump the © year when the page is next edited in a new year.
- **Research section:** we don't scan. If that ever changes, publish the scanner addresses,
  reverse DNS and method on the page *before* the first scan, and check the upstream's
  acceptable use policy first (Vultr does not allow scanning).
