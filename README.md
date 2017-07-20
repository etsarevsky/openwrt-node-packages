# OpenWrt Node.js Packages (nodejs)

## Description

OpenWrt Node.js Packages : for Chaos Calmer

Note: Testing target only ar71xx.

## License

See [LICENSE](LICENSE) file.

## Usage

Add follow line to feeds.conf or feeds.conf.default
```
src-git node https://github.com/nxhack/openwrt-node-packages.git;for-15.05
```

Run
```
./scripts/feeds update node
rm ./package/feeds/packages/node
rm ./package/feeds/packages/node-arduino-firmata
rm ./package/feeds/packages/node-cylon
rm ./package/feeds/packages/node-hid
rm ./package/feeds/packages/node-serialport
./scripts/feeds install -a -p node
```

## Note
Tested OpenWrt Chaos Calmer(15.05)

Node version v4.x 'Argon' (LTS)

uClibc is not well maintained.
* Need apply patches for compiling node v6.x & uppper.
   + https://github.com/artynet/openwrt-git/blob/openwrt-1505-setup-03/toolchain/gcc/patches/4.8-linaro/852-libstdcxx-uclibc-c99.patch
   + https://raw.githubusercontent.com/artynet/openwrt-git/openwrt-1505-setup-03/toolchain/uClibc/patches-0.9.33.2/L001-uClibc-add-execvpe-function.patch
   + https://raw.githubusercontent.com/artynet/openwrt-git/openwrt-1505-setup-03/toolchain/uClibc/patches-0.9.33.2/L002-libm_Add_missing_C99_float_ld_wrappers.patch
   + https://raw.githubusercontent.com/artynet/openwrt-git/openwrt-1505-setup-03/toolchain/uClibc/patches-0.9.33.2/L003-force-obstack-free-strong-alias.patch

ICU package is not available.

'HOST_BUILD_PREFIX' is not defined.
* Use 'STAGING_DIR_HOST'

'PKG_MD5SUM' is not supported SHA256 hash.

eudev package is not available.

**Illegal instruction issue**

If you are running nodejs on Atheros AR933x, You need to make a kernel with CONFIG_MIPS_FPU_EMULATOR=y.

## Modules that need build with '--build-from-source' option.
```
node-alljoyn
node-arduino-firmata		(serialport)
node-authenticate-pam
node-autobahn			(utf-8-validate, bufferutil)
node-bluetooth-hci-socket
node-cylon-firmata		(serialport)
node-firmata			(serialport)
node-fuse-bindings
node-hashtable
node-homebridge			(mdns [need select 'y'[*] libavahi-compat-libdnssd for InstallDev libdns_sd.so])
node-i2c-bus
node-ibmiotf			(utf-8-validate, bufferutil)
node-ideino-linino-lib
node-johnny-five		(serialport)
node-leveldown
#node-level			(leveldown)
node-mdns			[need select 'y'[*] libavahi-compat-libdnssd for InstallDev libdns_sd.so]
node-mknod
node-modbus
node-node-expat
node-node-hid
node-node-red			(bcrypt)
node-node-red-contrib-gpio	(serialport)
node-node-red-node-arduino	(serialport)
node-onoff
node-rpio
node-serialport
node-sleep
node-sqlite3
node-statvfs
node-usb
```
Other modules can be installed by 'npm install'.
