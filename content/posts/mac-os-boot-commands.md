+++
categories = ["Mac OS"]
date = 2020-05-24T01:33:32Z
description = "Mac OS special keyboard shortcuts for booting into repair utilities"
featuredImage = "/images/mac_boot_screen.jpg"
hiddenFromHomePage = true
lastmod = 2020-05-24T01:33:32Z
lightgallery = true
subtitle = ""
tags = ["Tips & Tricks", "Mac OS"]
title = "Mac OS Boot Commands"
toc = true

+++
<!--more-->

### Boot Into Recovery

Press **⌘ Command + R**

{{< image src="/images/screenshot_boot_utilities_screenshot.jpg" caption="OSX Rocovery Utilities" src-l="/images/screenshot_boot_utilities_screenshot.jpg" linked=true  >}}

### Boot Drive Selection Menu

Press **⌥ Option** key on boot

### Apple Diagnostics/Hardware Test

Hod **D** key while machine boots

{{< image src="/images/apple_hardware_tests.jpg" caption="OSX Rocovery Utilities" src-l="/images/apple_hardware_tests.jpg" linked=true  >}}

### Reset NVRAM

Hold **⌥ Option + ⌘ Command + P + R** while booting

\[NVRAM\]^(Nonvolatile RAM) is how your Mac saves specific preferences when it is powered off. NVRAM handles volume, resolution, time zone settings, and startup disk.

### Reset the SMC

Resetting the \[SMC\]^(system management controller) can help with many hardware issues. If your fans are running even when your Mac is idle is a good example. It also addresses issues with sleep, the ambient light sensor, and keyboard backlight. It may fix some issues with your Mac’s battery charging.

> The instructions for resetting SMC were copied verbatim from [Apple Support](https://support.apple.com/en-us/HT201295)

#### For Macs with a T2 chip

1. Shut down your Mac.
2. On your built-in keyboard, press and hold all of the following keys. Your Mac might turn on.
   * **Control ⌃** on the left side of your keyboard
   * **Option ⌥** on the left side of your keyboard
   * **Shift ⇧** on the right side of your keyboard
3. Keep holding **all three keys** for 7 seconds, then press and hold the **power button** as well. If your Mac is on, it will turn off as you hold the keys.
4. Keep holding **all four keys** for another 7 seconds, then release them.
5. Wait a few seconds, then press the **power button** to turn on your Mac.

#### For all other Macs

1. [Shut down your Mac](https://support.apple.com/kb/HT201150).
2. On your built-in keyboard, press and hold all of these keys:
   * **Shift ⇧** on the left side of your keyboard
   * **Control ⌃** on the left side of your keyboard
   * **Option ⌥** on the left side of your keyboard
3. While holding **all three keys**, press and hold the **power button** as well.
4. Keep holding **all four keys** for 10 seconds.
5. Release all keys, then press the **power button** to turn on your Mac.

### Verbose Boot

Hold **⌘ Command + V** while booting.

### Safe Mode

Hold **⌃ Shift** Key while booting.

### Single User Mode/Boot Into Shell

Hold **⌘ Command + S** while booting.

This drops you to a command line with root privileges.

### Target Disk Mode

Hold **T** while booting.

If you want to copy data off of a Mac, Target Disk Mode is useful. Hold **T** when booting your Mac and then connect your Mac to another Mac using a Thunderbolt, Firewire, or USB-C. You can then use Migration Assistant or even Finder to copy the files that you need. This mode has a somewhat limited application, but it is one that can be helpful.