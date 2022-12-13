### UIScale
Type: plist integer, 8 bit
Failsafe: -1
Description: User interface scaling factor.

Corresponds to 4D1EDE05-38C7-4A6A-9CC6-4BCCA8B38C14:UIScale variable.
```shell
1 — 1x scaling, corresponds to normal displays.
2 — 2x scaling, corresponds to HiDPI displays.
-1 — leaves the current variable unchanged.
0 — automatically chooses scaling based on the current resolution.
```

Note 1: Automatic scale factor detection works on the basis of total pixel area and may fail on small HiDPI displays, 
in which case the value may be manually managed using the NVRAM section.

Note 2: When switching from manually specified NVRAM variable to this preference an NVRAM reset may be needed.