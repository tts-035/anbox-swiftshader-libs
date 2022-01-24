# anbox-swiftshader-libs

archive contents


lib
    └── anbox
        └── swiftshader
            ├── libEGL.so
            ├── libGLES_CM.so
            └── libGLESv2.so

3 directories, 3 files

put this libs to anbox snap path /lib/anbox/swiftshader/


you need to repack anbox snap

first install squashfs-tools

apt install squashfs-tools


then

sudo snap disable anbox
unsquashfs anbox_xxx.snap
###copy libs to /squashfs-root/lib/anbox/swiftshader/

mksquashfs squashfs-root anbox_xxx_mod.snap

###replace the original anbox_xxx.snap with ambox_xxx_mod.snap
###dont forget to rename it to anbox_xxx.snap without "mod"
sudo snap enable anbox

###test with anbox session-manager
anbox session-manager
###there are should not be any errors

