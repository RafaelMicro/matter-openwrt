# Matter OpenWrt Feed

This repository is an [OpenWrt](https://openwrt.org) feed that packages [Matter](https://github.com/project-chip/connectedhomeip) software components for the OpenWrt operating system. It forms part of a reference implementation for Matter device types in the Routers & Access Points category.

Matter is a unified, open-source application-layer connectivity standard built to enable developers and device manufacturers to connect and build reliable, and secure ecosystems and increase compatibility among connected home devices. Visit [buildwithmatter.com](http://buildwithmatter.com) to learn more.

## Usage

This repository is intended to be included as a package feed in an OpenWrt buildroot, and familiarity with the configuration and use of the OpenWrt build system is assumed in the following instructions. Please refer to the [OpenWrt Developer Guide](https://openwrt.org/docs/guide-developer/start) for general guidance on building an OpenWrt system.

Note that this repository is aimed primarily at Matter implementers and OpenWrt integrators, and provides source packages only.

### Adding the feed

Add the following line to `feeds.conf` (ensure the OpenWrt `packages` feed is also present; it's definition can be copied from `feeds.conf.default` if necessary):

```
src-git chip https://github.com/RafaelMicro/matter-openwrt.git
```

Run the following commands to fetch the feed and install it into the build:

```
$ ./scripts/feeds update packages chip
$ ./scripts/feeds install -a -p chip
```

### Build configuration

For a minimal configuration, overwrite the `.config` file with the following lines and then run `make defconfig`:

```
CONFIG_PACKAGE_chip=y

#
# Configuration for Matter Host
#
CONFIG_CHIP_TOOL=y
CONFIG_CHIP_OTA_PROVIDER=y
CONFIG_CHIP_BRIDGE=y
# end of Configuration for Matter Host
```

