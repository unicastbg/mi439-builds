# Mi439 Builds

Unofficial LineageOS 23.2 for Xiaomi Mi439 variants.

## Downloads

Use the [latest normal release](https://github.com/unicastbg/mi439-builds/releases/tag/mi439-23.2-20261015). The one-time [migration ZIP remains in the original release](https://github.com/unicastbg/mi439-builds/releases/tag/mi439-23.2-20261005-test):

- Normal ROM: `lineage-23.2-20261015-UNOFFICIAL-Mi439.zip`.
- Standalone recovery: `recovery.img` in the latest release.
- Migration ZIP: filename containing `migration`, only for the first transition from official LineageOS 23.2.
- Verify each download using its matching `.sha256` file. GitHub's Source code archives are not ROM packages.

## Installation and Updates

Back up important data first. These migration steps are for an existing official LineageOS 23.2 installation, not stock MIUI or an older Android release. Install Android Platform Tools on the computer, enable USB debugging on the phone, authorize the computer, and put both downloaded ZIPs in the directory where you run the commands. If USB debugging is unavailable, enter recovery with the phone's hardware keys; ADB on the computer is still required to sideload the ZIPs.

### Migration From Official LineageOS 23.2

1. With the phone booted and connected by USB, check the connection and enter recovery:

   ```sh
   adb devices
   adb reboot recovery
   ```

2. In recovery, select **Apply update > Apply from ADB**, then run:

   ```sh
   adb sideload lineage-23.2-20261005-UNOFFICIAL-Mi439-migration.zip
   ```

3. Wait for final install status 0. Reboot to Android once and confirm your apps and files are present. After Android has fully booted and ADB is available again, return to recovery:

   ```sh
   adb reboot recovery
   ```

4. Select **Apply update > Apply from ADB** again, then install the latest normal ROM:

   ```sh
   adb sideload lineage-23.2-20261015-UNOFFICIAL-Mi439.zip
   ```

5. Wait for final install status 0, then select **Reboot system now** in recovery. The normal ROM installs community recovery for future OTA updates.

### Already On A Community Normal Build

Do **not** repeat migration. Use the built-in Updater for OTA releases. For a manual update, boot recovery with `adb reboot recovery`, select **Apply update > Apply from ADB**, then run:

```sh
adb sideload lineage-23.2-20261015-UNOFFICIAL-Mi439.zip
```

Wait for status 0 and select **Reboot system now**.

Do not wipe or format data. Do not reinstall older recovery-fixed or ota-test2 packages; their recovery certificate archive is defective. See the release notes for recovery instructions and initial official-recovery signature warnings.

Migration and automatic OTA were tested on one Redmi 8A without Google Apps, microG or Magisk. The October 10 normal build installed through OTA without issues or data loss and corrected the System updates layout and full build date. The latest October 15 build includes WebView and Bluetooth updates plus short release-note support, but has not yet been phone-tested. ADB confirmed the newer build, successful recovery installation log and corrected recovery checksum. Other variants, add-ons and hardware functions are not comprehensively validated; data preservation is not guaranteed.

After the one-time migration and corrected recovery transition, future community releases use Settings > System > Updater. The [Mi439 OTA feed](https://unicastbg.github.io/mi439-ota/Mi439-23.2.json) offers the latest normal release.

## Kernel Source

[Exact kernel source revision](https://github.com/LineageOS/android_kernel_xiaomi_msm8937/tree/704f6f08135c39728fcbe6f94b3956d911bb1801), branch `lineage-23.2`. The ROM's saved build manifest pins this commit; no local kernel-source modifications were used.

ROM ZIPs are release assets, not committed to Git. Signing keys remain private.
