# Aptus 2019 - Build on Rock64 Single Board Computer(SBC)
## Build Aptus image from scratch

### Download on this image and write it to a MicroSD card: 
Source:https://github.com/ayufan-rock64/linux-build/releases/download/0.9.14/stretch-minimal-rock64-0.9.14-1159-arm64.img.xz (243MB)

#### Extract .xz files
```console
$ sudo apt-get install xz-utils
$ unxz file.xz
```

#### Write image to a MicroSD card
Source: https://www.raspberrypi.org/documentation/installation/installing-images/
* DD command
```console
$sudo dd if=/path/to/sdcard.img of=/dev/sd(a,b,c) bs=4096 status=progress
$sudo sync
```
* Etcher
Source: https://www.balena.io/etcher/
* win32diskimager
Source: https://sourceforge.net/projects/win32diskimager/

### Boot Aptus/Rock64 for the first time
#### Hardware Required
* Aptus/Rock64 board
* A microSD card with Ayunfan Rock64 Strech minimal image
* A HDMI capable monitor and HDMI cable
* Wireless/Wired keyboard
* Power bank or AC Adapter
* USB Wifi adapter, rtl8188eu https://store.pine64.org/?product=usb-wifi-802-11bgn-rtl8188eu-for-rock64

### Wifi Module
#### Two USB WiFi Adapters
* rtl8188eu https://store.pine64.org/?product=usb-wifi-802-11bgn-rtl8188eu-for-rock64
* rtl8812au https://store.pine64.org/?product=rock64-usb-3-0-dual-band-1200mbps-wifi-802-11abgnac-rtl8812au-adapter

### Install packages
```console
sudo apt install phpmyadmin
sudo apt install shellinabox
sudo apt install iftop
sudo apt install htop
```
### Configurations
#### hostapd.conf
```bash
interface =wlan0
driver=nl80211
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
hw_mode=g
country_code=US
channel=11
auth_algs=1
wpa=0
macaddr_acl=0
disassoc_low_ack=0
#ieee80211n=1
#wmm_enabled=1
#ht_capab=[HT40-][SHORT-GI-20][SHORT-GI-40]
```
#### dhcpd.conf
```bash
static ip_address=192.168.169.2
static routers=192.168.169.2
```
#### dnsmasq.conf
```bash
dhcp-range=192.168.169.10,192.168.169.250,2h
dhcp-option=3,192.168.169.2
```

### Install Jupter Notebook


