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
6. Publish GitHub release `v1.0.0`. The **Deploy free plugin to WordPress.org** workflow copies the code to SVN `trunk`, tags `1.0.0` and uploads `wordpress-org/` to `assets/`.
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
