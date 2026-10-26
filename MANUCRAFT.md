# MANUCRAFT customizations (PdfCraft)

This fork (`netoonine/pdfcraft`, branch `manucraft`) = upstream `storytold/pdfcraft` + the changes below.
Every line we change in an upstream file is marked `MANUCRAFT` (`grep -rn MANUCRAFT apps crates`).
On a sync conflict keep upstream's code and re-apply our marked lines.

## 1. The releases page link points at our fork

**What:** the "releases page" link in Help › Check for Updates opens `netoonine/pdfcraft` releases.

| File | Hook |
|---|---|
| `crates/ui-egui/src/updates.rs` | `RELEASES_PAGE` |

Since upstream #4654 (2026-10-25) the update check and the self-update run through `craft_update` (craft-libs),
which reads `craft_update::suite::PDFCRAFT` (storytold) and only installs builds signed with Storytold's Apple team.
Our old hook in `apps/pdfcraft/src/updates.rs` went away with that file. The user chose (2026-10-26) to keep the
official in-app update as is, so there is no hook on the updater itself.

**Test:** `cargo test -p pdfcraft-ui-egui --test it updates`.

Not changed (on purpose): the Help › GitHub link (`crates/engine/src/links.rs`) still opens the original project.
