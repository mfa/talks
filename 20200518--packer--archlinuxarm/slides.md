class: center, middle

# Packer on ArchLinuxARM

Andreas Madsack (mfa)

datenobservatorium<br/>
2020-05-18

---

## Problem

- ready to use images for RaspberryPI with ArchlinuxARM
- wifi configured, ssh-keys already deployed, essential packages installed

---

## Before

- one big shell script
- extracts onto sdcard
- adds files for wifi, ssh-keys
- no easy possibility to install packages

---

## ArchlinuxARM

- alternative to debian-based Raspbian
- newer packages (i.e. kernel 5.4.x, python 3.8.x)
- less magic, more real Linux
- https://archlinuxarm.org/

---

## Packer.io

- from HashiCorp (terraform, vagrant, …)
- "Build Automated Machine Images"
- specification by json not by shell code
- https://www.packer.io/

---

## qemu / docker

- emulation of ARM architecture on x86 using qemu
- bundled in docker so ready to use without installing qemu
- could be used with bash script too. not that easy to setup!


---

## Solution

- https://github.com/mkaczanowski/packer-builder-arm
- ready to use builders for ARM, archlinuxarm, raspbian, …
- configured by json bundle files
- https://github.com/mkaczanowski/packer-builder-arm/tree/master/boards


---

## Example

```
docker run --rm --privileged -v /dev:/dev -v ${PWD}:/build \
  mkaczanowski/packer-builder-arm build boards/raspberry-pi/archlinuxarm.json
```


---

## Write image on sdcard

```
sudo dd bs=4M if=raspberry-pi.img of=/dev/sdX conv=fsync
```

(change /dev/sdX to your device)

---

## additional

- using **yaml** for config, not json  
  smaller files, better readability, **comments**  
- script that combines builder, provisioners and variables based on target
- secrets directory not checked in atm
- in secrets are: ssh-pubkeys, wifi-credentials, tinc-rsa-keys

---

## thanks
