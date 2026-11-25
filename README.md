# OnePlus 13T Camera Fix for OxygenOS 17.0.0.201

My fork of [kinginu's OnePlus 13T Camera Fix](https://github.com/kinginu/oneplus13t-fix-camera), updated for the Chinese OnePlus 13T (PKX110) after converting it to OnePlus 13s OxygenOS `CPH2723_17.0.0.201`.

The module mounts selected ODM files from ColorOS over their OxygenOS counterparts at boot. This update refreshes 35 camera files from `PKX110_17.0.1.201(CN01) F.18`. I installed the module through Magisk and confirmed the camera works on my phone running `CPH2723_17.0.0.201`.

## Installation

1. Download `oneplus13t-fix-camera-CPH2723_17.0.0.201.zip` from the [releases page](https://github.com/Mainz0412/oneplus13t-fix-camera/releases).
2. In Magisk, open **Modules**, choose **Install from storage**, select the ZIP, and reboot.

The ZIP keeps the original module ID, so Magisk installs it in place of the existing camera fix. If you run into problems, disable the module in Magisk and reboot.

## Known Issue: Photos Turn Black After Capture (KernelSU / APatch)
If a captured photo looks fine for about a second and then fades to pure black — while **Pro mode, video recording, and third-party camera apps work normally** — your root manager is hiding this module's files from the camera app.

KernelSU and APatch unmount module files for apps that are not granted root (the "Umount modules" feature). The camera app's multi-frame post-processing then reads the original OxygenOS files instead of the ones provided by this module, fails, and saves a black image.

**Fix (no root grant needed):**
1. Open the KernelSU / APatch manager app.
2. Find the camera app (`com.oplus.camera`) in the app list and open its App Profile.
3. Uncheck **Umount modules** and save.
4. Restart the camera app (or reboot).

If the gallery shows the same behavior, repeat the steps for the Photos/Gallery app.

## Credits

Thanks to [kinginu](https://github.com/kinginu) for the original module and the ODM update method. This build was shared for the users following [upstream issue #35](https://github.com/kinginu/oneplus13t-fix-camera/issues/35).
