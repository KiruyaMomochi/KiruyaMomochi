## Windows
### Apps
shell:AppsFolder

### WSL

#### Get Host IP

```sh
ip route show default | grep --perl-regexp --only-matching '(?<=via )\S+'
```

#### LaTeX
##### texdoc: open with default Windows PDF viewer
```
viewer_pdf = (explorer.exe $(wslpath -w %s)) &
```
## Fiddler
### Android capture packet
about:config -> fiddler.certmaker.validdays = 90

### Trust User Certificate

#### Magisk

https://github.com/Magisk-Modules-Repo/movecert

#### Manual

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

## Crk

### Affnty serises
Search for "k3yg3n mesmer1ze"

## Git

### Using built-in SSH with Git on Windows 10

```config
[core]
    sshCommand = C:/WINDOWS/System32/OpenSSH/ssh.exe
```

https://www.jvandertil.nl/posts/2019-01-18_usingwindowssshwithgit/

### Set commiter date to author date

```bash
git filter-branch --env-filter 'export GIT_COMMITTER_DATE="$GIT_AUTHOR_DATE"' HEAD~6..HEAD 
```

### Sign previous commits

```bash
git rebase --exec 'git commit --amend --no-edit -n -S' -i 8fd7b22
```

https://stackoverflow.com/questions/41882919/is-there-a-way-to-gpg-sign-all-previous-commits

## SSH

### SSH config directory

```ssh-config
Include config.d/*
```

### SSH through proxy

Windows

Install `nmap` to get `ncat`.

```ssh-config
Host *
  # For Socks 5 proxy
  ProxyCommand ncat --proxy-type socks5 --proxy localhost:1089 %h %p
  # For HTTP proxy
  ProxyCommand ncat --proxy localhost:1089 %h %p
```

Linux

```ssh-config
Host *
  # For Socks 5 proxy
  ProxyCommand /usr/bin/nc -x 172.23.176.1:1089 %h %p
```

## Java

### Soot

#### Use Kotlin

```
java -cp "soot.jar" soot.Main -pp -cp '...\JetBrains\...\plugins\Kotlin\kotlinc\lib\kotlin-stdlib.jar;.' MainKt
```

## Cloud

### Oracle

#### Ubuntu Firewall problem

Opening port 80 on Oracle Cloud Infrastructure Compute node
https://stackoverflow.com/questions/54794217/opening-port-80-on-oracle-cloud-infrastructure-compute-node

## CUDA

### CMake + CUDA + VS2022 Temporary Solution

1. Open `%PROGRAMFILES%\NVIDIA GPU Computing Toolkit\CUDA\v11.5\extras\visual_studio_integration\MSBuildExtensions`.
2. Open `CUDA 11.5.props`, version number may differ.
3. Modify `BuildCommandLineTemplate` by appending ` -allow-unsupported-compiler`.
4. Copy all these 4 files into `%PROGRAMFILES%\Microsoft Visual Studio\2022\Preview\Msbuild\Microsoft\VC\v170\BuildCustomizations`.
5. Try build again.

