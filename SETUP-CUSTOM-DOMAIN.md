# Moving support to lineup.bigleap.app

The App Store support URL currently points at `r-varun.github.io/lineup-support`,
which is live and Big Leap branded. To serve it from bigleap.app instead, two
steps, in this order. **Order matters**: adding the CNAME file before DNS
resolves takes the current support URL offline, and it is on a live submission.

## 1. DNS (you)

At whoever hosts bigleap.app DNS, add:

```
lineup    CNAME    r-varun.github.io.
```

Verify it before continuing:

```bash
dig +short lineup.bigleap.app
```

## 2. Point Pages at it (me, or you)

```bash
cd <this repo>
echo "lineup.bigleap.app" > CNAME
git add CNAME && git commit -m "Serve support from lineup.bigleap.app" && git push
```

Then in GitHub → Settings → Pages, tick **Enforce HTTPS** once the certificate
is issued (a few minutes).

## 3. Update the listing

Support URL becomes `https://lineup.bigleap.app/`, privacy policy URL becomes
`https://lineup.bigleap.app/privacy.html`. Both are editable while the version
is in review.

## Why not bigleap.app/lineup

That would be cleaner, but it needs a page deployed on the existing Big Leap
host, which is not GitHub Pages (`216.150.1.1`). If you would rather do that,
the two HTML files and the stylesheet here are self-contained and can be copied
straight into that site; then the support URL is `https://bigleap.app/lineup`
and this repo can be archived.
