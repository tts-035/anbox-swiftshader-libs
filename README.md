# Anbox swiftshader libs 
## Archive contents



```
lib
    └── anbox
        └── swiftshader
            ├── libEGL.so
            ├── libGLES_CM.so
            └── libGLESv2.so
```
3 directories, 3 files


Put this libs to anbox snap path /lib/anbox/swiftshader/ if you want this to work:
https://docs.anbox.io/userguide/advanced/software_rendering.html




You need to repack anbox snap
-----------------------------

Snaps can be found at /var/lib/snapd/snaps

First install squashfs-tools

```
sudo apt install squashfs-tools
```


Then

```
sudo snap disable anbox
unsquashfs anbox_xxx.snap
```
Copy libs to /squashfs-root/lib/anbox/swiftshader/

```
mksquashfs squashfs-root anbox_xxx_mod.snap
```

Replace the original anbox_xxx.snap with ambox_xxx_mod.snap

Dont forget to rename it to anbox_xxx.snap without "mod"

```
sudo snap enable anbox
```

Test it with anbox session-manager

```
anbox session-manager
```
There are should not be any errors

