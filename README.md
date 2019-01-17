# twrp_samsung_kanas3gnfcxx
TWRP Device configuration for Samsung Galaxy Core II SM-G355H

android_device_samsung_kanas3gnfc
===================================

## Instructions how to build

I assume you have already set up your build environment
but if you haven't then please skim this
[guide](https://forum.xda-developers.com/showthread.php?p=32965365#post32965365).
It's a lengthy guide, but please read at least the first few paragraphs.

**A word of warning, I did use the omni's source as indicated in the guide**

After `repo sync` command completes,
create the folder device/samsung/kanas then
copy the contents of which you downloaded from here.

Then run these commands in terminal from your *source root directory*.

        . build/envsetup.sh
        lunch omni_kanas-userdebug
        make recoveryimage

*source root directory* means the directory where you've run `repo sync`
or that folder with hidden folder named `.repo` inside it.

The build should start in which after you will find your `recovery.img` in
`out/target/product/kanas` relative from your source root directory.

________
### ODIN package
To make it flashable via ODIN, you have to repackage it as `recovery.tar.md5`.

Now back to the terminal, go to the `out/target/product/kanas` directory.
Suppose you're in your source root directory, you can run

         cd out/target/product/kanas

Then to repackage, run these:

        tar -H ustar -c recovery.img > recovery.tar
        md5sum -t recovery.tar >> recovery.tar
        mv recovery.tar recovery.tar.md5
        
Congratulations, you've gotten a `recovery.tar.md5` ready to be flashed via ODIN.
Select it in the PDA file entry, then flash.

Happy building.

*~Draft*


