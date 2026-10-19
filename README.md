# Orion Kernel — Poco F4 (munch)

This repository is being assembled for the Xiaomi Poco F4 / Redmi K40S (munch).

## Source plan

- Official base: [MiCode Xiaomi Kernel OpenSource, `munch-s-oss`](https://github.com/MiCode/Xiaomi_Kernel_OpenSource/tree/munch-s-oss)
- Known-good reference: [Cypher-Emm kernel tree](https://github.com/Cypher-Emm/kernel_xiaomi_sm8250_mod), v1.3 baseline only for selected changes
- Device target: Poco F4 / munch, Snapdragon 870
- Desired optional integrations: BakaSU and SUSFS, subject to source compatibility review

## Current status

**This repository is not yet a complete kernel source tree and does not currently build a flashable kernel.** The initial commit adds a GitHub Actions source-audit workflow so the first run can report what is present in the official Xiaomi source and what is still missing. Do not flash any artifact from this repository.

The Xiaomi source branch has known reports about missing device techpack code. Display, camera, and audio components must be sourced from a compatible munch kernel tree and integrated with their Kconfig/Makefile dependencies; copying directories without resolving those dependencies is not a safe fix.

## Run the audit

1. Open the **Actions** tab.
2. Select **Source audit**.
3. Click **Run workflow** on `main`.
4. Download the `orion-source-audit` artifact and inspect `source-audit.md`.

This audit checks source completeness only; it is not a build workflow.

## Next steps before a real build

1. Import the full official kernel source and preserve its licensing and attribution.
2. Restore compatible missing techpack code and validate build integration.
3. Compare against the v1.3 device tree and port only reviewed fixes.
4. Review BakaSU/SUSFS changes against this kernel's Android version and security interfaces.
5. Add a build workflow only after the correct munch defconfig, toolchain, packaging and boot image requirements are verified.
6. Build and test on a recoverable device before treating an artifact as flashable.

## Licensing

Kernel code is primarily GPL-2.0; individual files and imported components may have different notices. Preserve upstream license files and notices when source is imported.
