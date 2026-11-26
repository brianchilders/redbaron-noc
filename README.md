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
| `CNAME` | Custom domain for GitHub Pages (`www.redbaron.net`). |
| `.nojekyll` | Turns off Jekyll so that `.well-known/` gets published. |
| `.well-known/security.txt` | Security contact file ([RFC 9116](https://www.rfc-editor.org/rfc/rfc9116)). |

To change the site, edit the files and push to `main`. Pages redeploys within a minute or two.

## Maintenance checklist

- **Every year:** update the `Expires:` date in `.well-known/security.txt`.
  It's currently `2027-11-25`. RFC 9116 says to keep it less than a year out,
  so set a reminder for early November.
- **Keep the contacts in sync with ARIN.** The email on the page and in
  `security.txt` (`childers@redbaron.net`) and the phone number must match the ARIN POC
  [BC117-ARIN](https://rdap.arin.net/registry/entity/BC117-ARIN) and the Abuse POC.
  ARIN also sends an annual POC validation email, so answer it.
- **Network section:** replace the `x.x.x.0/24` placeholder with the real
  prefix. Fill in the ASN when it's assigned, and add a PeeringDB link once
  the PeeringDB entry exists.
- **Footer:** bump the © year when the page is next edited in a new year.
