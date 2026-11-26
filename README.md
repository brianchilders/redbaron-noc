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

Anything not yet final is tagged on the page with an amber **PLACEHOLDER**,
**PLANNED** or **NOT ACTIVE YET** tag. To find them all, search `index.html` for `class="ph"`.
Remove the "This page is being completed" banner once they're all gone.

- [ ] **Role aliases:** create `noc@`, `abuse@`, `security@`, `hostmaster@` and `postmaster@`
      in Google Workspace, all delivering to childers@redbaron.net.
- [ ] **ARIN role POC:** create a role POC that uses the role addresses and assign it as the
      Org's NOC, Tech and Abuse POC. BC117-ARIN stays as Admin.
      Then make the aliases into `mailto:` links on the page, remove their tags,
      add the role POC handle, and switch the abuse policy address to `abuse@`.
- [ ] **security.txt:** add `Contact: mailto:security@redbaron.net` as the first Contact line.
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
  POC records ([BC117-ARIN](https://rdap.arin.net/registry/entity/BC117-ARIN) and the role POC).
  If you change one, change the other. ARIN sends an annual POC validation email, so answer it.
- **Keep `geofeed.csv` in sync with the Network section** whenever prefixes are added or move.
- **When you review the page**, update the "Last reviewed" date in the footer.
- **Footer:** bump the © year when the page is next edited in a new year.
