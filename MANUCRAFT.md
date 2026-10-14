# MANUCRAFT customizations (PdfCraft)

This fork (`netoonine/pdfcraft`, branch `manucraft`) = upstream `storytold/pdfcraft` + the changes below.
Every line we change in an upstream file is marked `MANUCRAFT` (`grep -rn MANUCRAFT apps crates`).
On a sync conflict keep upstream's code and re-apply our marked lines.

## 1. Help › Check for Updates looks at our fork

**What:** the update check and the releases page point at `netoonine/pdfcraft` instead of `storytold/pdfcraft`,
so PdfCraft never offers the official build over the MANUCRAFT one.

| File | Hook |
|---|---|
| `apps/pdfcraft/src/updates.rs` | `LATEST` (GitHub API latest release URL); the two URLs in the test `answers_are_read_and_only_our_release_pages_are_offered` |
| `crates/ui-egui/src/updates.rs` | `RELEASES_PAGE` |

**Test:** `cargo test -p pdfcraft updates`.

Not changed (on purpose): the Help › GitHub link (`crates/engine/src/links.rs`) still opens the original project.
