## WSL
### LaTeX
#### texdoc: open with default Windows PDF viewer
```
viewer_pdf = (explorer.exe $(wslpath -w %s)) &
```
## Fiddler
### Android capture packet
about:config -> fiddler.certmaker.validdays = 90


(From https://gist.github.com/gpsarkar/ceecdba56c995737c7e637beace8e3c8#file-fiddler-capture-https-android-emulator-L4-L18)
```
Install toot certificate from `http://ipv4.fiddler:8888`

The certificate will now be located in /data/misc/user/0/cacerts-added/.

Remount /system R/W as root if you haven't already (mount -o remount,rw /system).

    adb shell
    su
    mount -o remount,rw /system

Move the .0 file to /system/etc/security/cacerts/ and chmod the file to 644.

    cd /data/misc/user/0/cacerts-added/
    mv 269953fb.0 /system/etc/security/cacerts/269953fb.0
    
    chown root:root /system/etc/security/cacerts/*
    chmod 644 /system/etc/security/cacerts/*
    chcon u:object_r:system_file:s0 /system/etc/security/cacerts/*
```

Also ref. https://blog.ropnop.com/configuring-burp-suite-with-android-nougat/
