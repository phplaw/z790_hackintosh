# z790_hackintosh
This document for making a Hackintosh system, It is just for hobby / research do not use for any commercial purporse.
The bootloader using for this Hackintosh is `Opencore`

NOTICE: Since `Intel Raptor Lake` CPU is not supported by Apple, When doing hackintosh with this kind of CPU, You have to Fake CPU 
So It requires us add `Cpuid1Data` & `Cpuid1Mask` for fake CPU that support by Apple.

There are some example for those value
```bash
55060A00 00000000 00000000 00000000

FFFFFFFF 00000000 00000000 00000000

```
```bash
C3060300 00000000 00000000 00000000
FFFFFFFF 00000000 00000000 00000000
```

### For making OpenCore Boot we need to generate `PlatformInfo` that close to our Hardware specs (Desktop & Laptop)

For setting up the **SMBIOS** info, we will need this tool `GenSMBIOS` or just using app `OpenCore Configurator` are fine.

Some OpenCore Variable we need to have an eye on them are
SecureBootModel => Default, Disabled
AppleXcpmCfgLock => TRUE/FALSE

`boot-args`: `-v keepsyms=1 debug=0x100 alcid=1 e1000=0 agdpmod=pikera`

`Misc > Boot| Debug` => `Target:67 ...`

`Misc > Security` => `SecureBootModel:Default, Disabled` `(Dmg Loading = Signed|Disabled)`
### After complete install hackintosh, you have to do some fix for your system. Below are some usual issues: 
[# Optimizing Power Management](https://dortania.github.io/OpenCore-Post-Install/universal/pm.html)

[# Fixing CFG Lock](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html#what-is-cfg-lock)


For Upgrade OpenCore, just need to download latest version and replace these files in your EFI folder

```shell
EFI/BOOT/BOOTx64.efi
EFI/OC/OpenCore.efi
EFI/OC/Drivers/OpenRuntime.efi
```
Same way we could replace debug version with release version by replace these file
```shell
# Replace the following files with the release versions (opens new window)(if previously using DEBUG versions):
EFI/BOOT/BOOTx64.efi
EFI/OC/OpenCore.efi
EFI/OC/Drivers/OpenRuntime.efi
```
For futher works after installed hackintosh, recommend to read this https://dortania.github.io/OpenCore-Post-Install/#how-to-follow-this-guide
If you do not complete install your hackintosh, then you have to read this https://dortania.github.io/OpenCore-Install-Guide/

We also need to read this for understand how to debug in Opencore [OpenCore Debugging](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html#file-swaps)