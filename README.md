# Auxora OS 1.0 — AAOS/AOSP ARM64 GSI

Auxora OS is an automotive system UI/product layer intended to be built inside AOSP/AAOS.
This repository is not a prebuilt binary ROM by itself. The build workflow produces the
flashable `system.img` (GSI) from an AOSP source checkout.

## Target

- ARM64
- AOSP / Android Automotive OS
- GSI / Project Treble development target
- Native Kotlin system launcher
- Soong (`Android.bp`)
- Vehicle access through Android Car APIs; hardware-specific VHAL remains vendor-side

## Integrating in an AOSP checkout

Copy this repository to:

    vendor/auxora/

Then from the AOSP root:

    source build/envsetup.sh
    lunch auxora_gsi_arm64-userdebug
    m -j$(nproc)

Primary output:

    out/target/product/generic_arm64/system.img

Depending on the selected AOSP branch/product, additional partition images may also be emitted.

## Important

A GSI only covers the generic Android system side. A production head unit still needs
hardware-specific bootloader, kernel, device tree, vendor partition, display/audio/touch
drivers, Bluetooth/Wi-Fi stack integration, VHAL implementation, SELinux policy and signing.
