# Mi439 Builds

Unofficial LineageOS 23.2 for Xiaomi Mi439 variants.

## Downloads

Use the [latest normal release](https://github.com/unicastbg/mi439-builds/releases/tag/mi439-23.2-20261010). The one-time [migration ZIP remains in the original release](https://github.com/unicastbg/mi439-builds/releases/tag/mi439-23.2-20261005-test):

- Normal ROM: `lineage-23.2-20261010-UNOFFICIAL-Mi439.zip`.
- Standalone recovery: `recovery.img` in the latest release.
- Migration ZIP: filename containing `migration`, only for the first transition from official LineageOS 23.2.
- Verify each download using its matching `.sha256` file. GitHub's Source code archives are not ROM packages.

## Installation and Updates

Back up important data. From official LineageOS 23.2: sideload the migration ZIP, boot Android once, then promptly sideload the normal ROM ZIP and wait for status 0. Do not wipe/format data or repeat migration on an existing community normal build.

Already on a community normal build: use Updater for the latest OTA. Do not reinstall older recovery-fixed or ota-test2 packages; their recovery certificate archive is defective. See the release notes for recovery instructions and initial official-recovery signature warnings.

Migration and automatic OTA were tested on one Redmi 8A without Google Apps, microG or Magisk. The latest normal build also installed through OTA without issues or data loss and corrected the System updates layout and full build date. ADB confirmed the newer build, successful recovery installation log and corrected recovery checksum. Other variants, add-ons and hardware functions are not comprehensively validated; data preservation is not guaranteed.

After the one-time migration and corrected recovery transition, future community releases use Settings > System > Updater. The [Mi439 OTA feed](https://unicastbg.github.io/mi439-ota/Mi439-23.2.json) offers the latest normal release.

## Kernel Source

[Exact kernel source revision](https://github.com/LineageOS/android_kernel_xiaomi_msm8937/tree/704f6f08135c39728fcbe6f94b3956d911bb1801), branch `lineage-23.2`. The ROM's saved build manifest pins this commit; no local kernel-source modifications were used.

ROM ZIPs are release assets, not committed to Git. Signing keys remain private.
