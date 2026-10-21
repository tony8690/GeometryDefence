# Geometry Defense — GitHub Pages website

A standalone, dependency-free site. `index.html` is the marketing page; `support.html` has the contact address and FAQs; `privacy.html` describes the local-save, private iCloud backup and Apple StoreKit data flows, plus GitHub hosting. Assets are local; there are no fonts, analytics scripts, forms or external image services to configure. The game screenshot comes from Godot's native renderer using an isolated, in-memory profile.

## Configure before publishing

The public support email is **tony-dev86@outlook.com** and is already set on all three pages. Supply the actual Pages address when it is available:

```sh
python3 configure.py --email 'tony-dev86@outlook.com' --base-url 'https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/'
python3 check_site.py
```

Replace the uppercase GitHub username/repository values with your real Pages address. The configuration command preserves the public email, edits only this site's local files and prints the three URLs for App Store Connect. It does not create a repository or publish anything. The site address has not been supplied or verified yet; a passing local check does not establish that the site is live.

Review the policy and contact details before publication. The policy covers local saves, the private full-profile CloudKit backup, random Keychain purchase identifier, Apple purchases, optional support correspondence and GitHub Pages hosting. Cloud references are conditional on the installed build having the feature configured; do not advertise live recovery until Apple container registration/provisioning, Production schema deployment and signed-device backup/restore tests are complete. See the game’s `docs/CLOUD_SAVE.md` for exact setup and limitations. This site does not promise recovery of unsaved changes, generic restoration of finished consumables or removal of Keychain/cloud records on uninstall. Update it when actual data handling changes.

## Publish on GitHub Pages

1. Create or use the repository you want for this site.
2. Put the **contents of this `website/` folder** in the repository root, including `.nojekyll`, `index.html`, `support.html`, `privacy.html` and `assets/`.
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select your published branch (usually `main`) and **/(root)**, then Save.
5. Wait for deployment and open the actual HTTPS address displayed by GitHub. On your phone, check all three pages, the contact link and images. GitHub notes that publication can take up to ten minutes.
6. Use the live URLs in `SUBMISSION_URLS.txt` for **Marketing URL**, **Support URL** and **Privacy Policy URL**. Do not submit a local filesystem address or an unverified example URL.

Official setup: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

All links use relative paths, so user sites, project sites and custom domains work. If hosting this folder in an existing repository instead of copying its contents, configure a Pages workflow that uploads only this folder; branch publishing supports repository root or `/docs`, not an arbitrary `/website` directory.

## Preview locally

From this folder:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Open `http://127.0.0.1:8765/`, then check `/support.html` and `/privacy.html`. This preview is local only. Press Control-C in the terminal to stop it.

## App Store text

Copy-ready English (UK) text and measured field lengths are in the parent project's `docs/APP_STORE_METADATA.md`, with a separate copy included in the download package as `APP_STORE_COPY.txt`. Promotional text is 157 characters, description 2,349 characters and keywords 86 ASCII bytes. Check the final text in App Store Connect after any edits.

## Maintenance

Keep contact information monitored and current. The site's review copy describes current implemented features, not a promise of App Store release approval or purchase availability. No StoreKit prices are hard-coded into the marketing pages. Replace or update screenshots when the UI changes. This folder is ignored by Godot and excluded from the iOS game exports.
