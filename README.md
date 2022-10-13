# Dell 7559 Monterey
2022-10-13
- 不再维护
- 不再提供技术支持
- wifi 蓝牙 核显均未驱动，此EFI仅用于安装系统
---
*opencore version 0.8.4*

*bios version 1.2.2(i7) 1.0.1(i5)*

bios设置参考，感谢[江南小虫虫](https://segmentfault.com/a/1190000020642944?utm_source=tag-newest)博客指导
- 恢复BIOS默认设置 (开机按F2进入bios，按F9恢复默认设置)
- Advanced
  - VT for direct I/O —————— Disabled
  - SATA Operation —————— AHCI
  - SupportAssist System Resolution —————— OFF
- Security
  - Firmware TPM  —————— Disabled  
- Boot
  - Boot List Option —————— UEFI
  - Secure boot —————— Disabled
  - Load Legacy Option Rom —————— Disabled
