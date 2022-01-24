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

These files are taken from anbox beta snap v

Put this libs to anbox snap path /lib/anbox/swiftshader/ if you want this to work:
https://docs.anbox.io/userguide/advanced/software_rendering.html




You need to repack anbox snap
-----------------------------

Snaps can be found at /var/lib/snapd/snaps

1. First install squashfs-tools:

```
sudo apt install squashfs-tools
```


2. Then:

```
sudo snap disable anbox
unsquashfs anbox_xxx.snap
```
3. Copy libs to /squashfs-root/lib/anbox/swiftshader/:

```
mksquashfs squashfs-root anbox_xxx_mod.snap
```

4. Replace the original anbox_xxx.snap with ambox_xxx_mod.snap

Dont forget to rename it to anbox_xxx.snap without "mod". You can do it with

```
mv anbox_xxx_mod.snap anbox_xxx.snap
```

or through file manager

5. After that:

```
sudo snap enable anbox
```

6. Now you can test it with anbox session-manager:

```
anbox session-manager
```
There shouldn't be any errors

