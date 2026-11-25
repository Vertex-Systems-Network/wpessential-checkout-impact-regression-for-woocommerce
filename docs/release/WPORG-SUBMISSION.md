# WordPress.org submission checklist – free plugin

**Plugin:** WPEssential Checkout Impact Regression for WooCommerce · **Slug:** `wpessential-checkout-impact-regression-for-woocommerce` · **Version:** 1.0.0
**WordPress.org account:** `wpessential` (listed in `readme.txt` → Contributors)
**Plugin URI:** https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/wiki

## Ready in the repository (2026-11-12)

| Item | Where | State |
|---|---|---|
| Main file with full header (Name, URI, Version, Requires at least/PHP/Plugins, Author, License, Text Domain, WC headers) | `wpessential-checkout-impact-regression-for-woocommerce.php` | Done |
| `readme.txt` generated from `wordpress-org/readme.md` by `tools/readme-to-txt.php` (WPEssential readme system; checks Stable tag, ≤5 tags, ≤150-char summary, required sections incl. External services) | `wordpress-org/readme.md` | Done |
| GPL-2.0-or-later licence file | `LICENSE` | Done |
| Text domain = slug, all strings translatable, `languages/` folder | code | Done |
| No external calls, no tracking, no remote assets, no locked features | code review | Done |
| Data sanitised, capability + nonce checks on every REST route | code + runtime test (anonymous/subscriber 403) | Done |
| Uninstall keeps data by default, opt-in erase removes everything | runtime test | Done |
| Privacy exporter/eraser + suggested policy text | runtime test | Done |
| Icon 128/256, banner 772×250 / 1544×500, screenshots 1–7, Live Preview blueprint | `wordpress-org/` | Done |
| User documentation | `docs/wiki/` → GitHub Wiki (enable Wiki in repo settings first) | Pages done |
| Package ZIP without dev files | `./bin/build.sh` or CI artifact **free-plugin-package** | Done |
| Plugin Check (official action) | CI job **WordPress.org Plugin Check** | Historical pass (CI run 43103077615); rerun on renamed package |

## Owner steps (need your WordPress.org login)

1. Merge the pull request, then download `wpessential-checkout-impact-regression-for-woocommerce-1.0.0.zip` from the CI **free-plugin-package** artifact (or run `./bin/build.sh`).
2. Make sure the Plugin Check job is green. Fix any error it reports before uploading.
3. Log in as `wpessential` at <https://wordpress.org/plugins/developers/add/>, accept the guidelines and upload the ZIP. Confirm the slug shown is `wpessential-checkout-impact-regression-for-woocommerce`.
4. Answer the review email from the Plugins Team within 7 days. Reply from the same account; re-upload a fixed ZIP from the same page if asked.
5. After approval, add repository secrets `SVN_USERNAME` (= `wpessential`) and `SVN_PASSWORD` (an SVN application password from your WordPress.org profile).
6. After approval and credentials are configured, publish the approved GitHub version tag/release and manually run **Build free ZIP / optional WordPress.org deploy** on that tag with publishing checked. Alternatively opt in to automatic future release publishing by setting repository variable `WPORG_DEPLOY_ENABLED=true` before publishing a release. Default runs only build an artifact; the opt-in SVN job copies code to trunk/tags and stages directory assets.
7. Verify the [plugin wiki](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/wiki) is publicly readable before submission.

## Review notes to keep ready

- The plugin does not run checkout or create orders; it stores values the admin records.
- "WooCommerce" is used only in the "for WooCommerce" suffix; no WooCommerce logo in assets.
- The readme mentions the separate Pro add-on once; the free plugin contains no Pro code, upsell banners or license checks.

The final WordPress.org slug is subject to directory approval. Verify current package CI and Plugin Check before uploading; historical results do not cover the renamed package.

## Main branch verification — 2026-11-26

[CI run 45690435213](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/actions/runs/45690435213), commit `9e92db5bab1bf37807e0c07ad0194ce2c0366fa0`: lint and contracts on PHP 8.2/8.3/8.4, paired Playground integration on 8.2/8.4, the free ZIP build and official Plugin Check passed. [Download artifact 15058067104](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/actions/runs/45690435213/artifacts/15058067104) (outer artifact SHA-256 `53652a3de1de6d60204c152213c7d0d9a2358dce423f8ac28f3b24e5fe44e246`). Extract the installable ZIP and verify its included SHA-256 checksum. [Wiki sync run 45690435197](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/actions/runs/45690435197) passed; public page access was not independently verified.

The earlier [SVN deploy run 45687749046](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/actions/runs/45687749046) failed on the old commit because `SVN_USERNAME` was not configured. Do not retry or publish before directory approval and final slug assignment. Once approved, configure the SVN credentials securely as repository secrets and deploy from the approved source, not the old commit. No WordPress.org approval, listing or SVN publication has been verified.

The initial upload is the inner installable ZIP, not the Actions artifact wrapper. Keep the existing assets separate for approved SVN distribution. The official [plugin guidelines](https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/) and [developer FAQ](https://developer.wordpress.org/plugins/wordpress-org/plugin-developer-faq/) remain the submission authority.

## Verified paired compatibility — 2026-11-26

[Pro CI run 45705094936](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-pro-for-woocommerce/actions/runs/45705094936) passed on Pro head `55e05ab0482e3f25565e0fd3b10268c6514c76dc` (PR merge test) with Free `93832d7f4d38450b71a78d9a0b12082820d9f083`. Installed runtime versions were checked from logs:

| WordPress | WooCommerce | PHP | Paired integration |
|---|---|---|---|
| 7.0.9 | 11.2.2 | 8.3.36 | Pass |
| 7.0.9 | 11.3.1 | 8.3.36 | Pass |
| 7.1.5 | 11.2.2 | 8.3.36 | Pass |
| 7.1.5 | 11.3.1 | 8.3.36 | Pass |
| 7.1.5 | 11.3.1 | 8.2.35 | Pass |
| 7.1.5 | 11.3.1 | 8.4.27 | Pass |

PHP lint/contracts and both package builds also passed. Run 45704087895 previously detected an incorrect PHP fallback in the moving-latest tests; corrected blueprint pinning and retained runtime assertions. Update WC tested up to to 11.3; minimums and version remain unchanged. Evidence covers synthetic paired integration in Playground (SQLite), not full checkout E2E, every possible version combination or vendor QIT. Fresh CI on the header-updated packages is required. Pro artifact publication remains blocked while the repository is public.

## Package-only workflow fix (2026-11-26)

[Run 45718601754](https://github.com/Vertex-Systems-Network/wpessential-checkout-impact-regression-for-woocommerce/actions/runs/45718601754) built the ZIP and staged assets successfully, then failed because `SVN_USERNAME` was absent. This was an SVN publishing failure, not a package build failure. The workflow now separates an unconditional Free ZIP + SHA-256 artifact job from the explicit opt-in SVN job. Manual runs default to package-only; releases default to package-only unless `WPORG_DEPLOY_ENABLED=true` is set. Explicit publishing requires a matching version tag and both SVN secrets, checks the inner ZIP checksum, and deploys the extracted built package. Pull requests never publish. Actual SVN publication remains pending approval and owner credentials. No external publication or settings change was performed. Fresh PR CI is required.
