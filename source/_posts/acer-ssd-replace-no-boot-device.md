---
title: Laptop install SSD show error "No Bootable Device"
date: 2018-12-06 23:04:15
banner: /eric-blogs/images_posts/samsung-ssd.jpg
thumbnail: /eric-blogs/images_posts/acer-laptop-ssd-no-bootable-device.jpg
categories:
- Hardware
- SSD
tags:
  - Operating system
  - Boot
---

Sometimes, when you replace a storage drive on a laptop, you might expect such an error showing "No Bootable Device". In this case, it is just that you are in the wrong Boot mode. 

When your laptop starts, go to BIOS. Go to Boot tab and change your UEFI/BOIS Boot Mode from UEFI to Legacy. For normal SATA hard drives, it is OK to be in UEFI mode, but for SSD, in order for it to boot normally, you have to go back to Legacy mode. After this, restart and the laptop's operating system should turn on.
