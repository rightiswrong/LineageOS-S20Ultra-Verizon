# LineageOS on the Verizon Galaxy S20 Ultra (SM-G988U): feasibility

**Verdict: not possible today.** The bootloader on US Snapdragon S20 models
(SM-G988U and SM-G988U1) cannot be unlocked, and no public exploit exists.
Every route to LineageOS — a native port, a GSI, or even a custom recovery —
needs an unlocked bootloader first.

*Last checked: 12 October 2026.*

## The device

| | |
|---|---|
| Model | Samsung Galaxy S20 Ultra 5G, Verizon (SM-G988U) |
| SoC | Qualcomm Snapdragon 865 (SM8250, "kona") |
| Other variants | SM-G988B (Exynos 990, international), SM-G988N (Snapdragon, Korea), SM-G9880 (Snapdragon, HK/TW/CN) |

Note: the chip is the Snapdragon 865, not the 835 (that was the Galaxy S8).
The hardware itself is well supported by custom ROMs; it is not the problem.

## Why it is blocked

1. **No OEM unlock on US models.** Samsung's normal unlock flow (OEM unlocking
   toggle → long-press Volume Up in Download Mode) works on SM-G988B, SM-G988N
   and SM-G9880 only. On U, U1 and Canadian W models the option is absent or
   has no effect.
2. **Changing firmware doesn't help.** Flashing the unbranded U1 firmware onto
   a Verizon phone removes carrier apps but leaves the bootloader locked.
   Firmware from unlockable variants (N, 0, B) cannot be flashed onto a U
   device.
3. **No community workaround.** Unlike the Sonim XP8 (see
   [rightiswrong/LineageOS-Sonim-XP8-8800](https://github.com/rightiswrong/LineageOS-Sonim-XP8-8800)),
   where a leaked debug bootloader flashed over EDL allows unlocking, there is
   no public leaked engineering bootloader or EDL-based unlock for SM-G988U.
4. **Verified boot blocks the GSI route.** With the bootloader locked,
   Samsung's AVB will not boot an unsigned system, boot or recovery image, so
   the GSI approach used for the Sonim does not apply either.

Paid "bootloader unlock" services advertised for U models have no published,
verifiable method. Don't use them.

## Options

1. **Stay on stock, cleaned up.** Flash the latest U1 firmware with Odin to drop
   Verizon's apps, then remove further bloat with
   `adb shell pm uninstall --user 0 <package>` (no root needed). The phone's
   final update was Android 13 / One UI 5.1; security updates have ended.
2. **Use an unlockable S20 Ultra.** SM-G988N or SM-G988B can be unlocked
   officially, which makes a LineageOS GSI or device build possible. That
   would be a separate project.
3. **Wait for an exploit.** If a public bootloader unlock for SM-G988U appears,
   revisit this document; the Snapdragon 865 platform would then make a port
   realistic.

## Sources

- XDA: [Lineage Recovery for S20 Series (Snapdragon)](https://forum.xda-developers.com/t/recovery-lineage-recovery-for-s20-series-snapdragon.4084977/) — lists unlockable Snapdragon models; states US U/U1 cannot be unlocked
- DroidWin: [Unlock bootloader on Galaxy S20 series](https://droidwin.com/?p=5217) — US U/U1/W Snapdragon variants excluded
- Appuals: [How to root Samsung Galaxy S20 series](https://appuals.com/how-to-root-samsung-galaxy-s20-series/) — eligible model list
