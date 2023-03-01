# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2006-2011 OpenWrt.org

include $(TOPDIR)/rules.mk

ARCH:=i386
BOARD:=x86
BOARDNAME:=x86
FEATURES:=squashfs vdi vmdk vhdx pcmcia fpu boot-part rootfs-part
SUBTARGETS:=64 generic legacy geode 

KERNEL_PATCHVER:=5.15
KERNEL_TESTING_PATCHVER:=6.1

KERNELNAME:=bzImage

include $(INCLUDE_DIR)/target.mk

DEFAULT_PACKAGES += autocore-x86 automount base-files bash block-mount busybox ca-bundle coremark curl dnsmasq-full \
dropbear ds-lite e2fsprogs fdisk firewall fstools grub2-bios-setup htop kmod-8139cp kmod-8139too kmod-alx kmod-amazon-ena \
kmod-amd-xgbe kmod-bnx2 kmod-bnx2x kmod-button-hotplug kmod-drm-amdgpu kmod-drm-i915 kmod-e1000 kmod-e1000e kmod-forcedeth \
kmod-fs-vfat kmod-i40e kmod-iavf kmod-igb kmod-igbvf kmod-igc kmod-ipt-nat kmod-ipt-nat6 kmod-ixgbe kmod-lib-zstd \
kmod-mlx4-core kmod-mlx5-core kmod-mmc kmod-pcnet32 kmod-phy-broadcom kmod-r8125 kmod-r8168 kmod-sdhci kmod-tcp-bbr kmod-tg3 \
kmod-tulip kmod-usb-hid kmod-vmxnet3 libc libgcc libustream-wolfssl lm-sensors-detect logd lsblk luci-app-advanced \
luci-app-autoreboot luci-app-firewall luci-app-gpsysupgrade luci-app-opkg luci-app-upnp luci-app-wizard luci-base luci-compat \
luci-lib-fs luci-lib-ipkg mkf2fs mtd nano netifd odhcp6c odhcpd-ipv6only openssh-sftp-server opkg partx-utils pciutils ppp \
ppp-mod-pppoe procd procd-seccomp resolveip swconfig uci uclient-fetch urandom-seed urngd usbutils wget-ssl zram-swap

$(eval $(call BuildTarget))

$(eval $(call $(if $(CONFIG_ISO_IMAGES),SetupHostCommand,Ignore),mkisofs, \
	Please install mkisofs. , \
	mkisofs -v 2>&1 , \
	genisoimage -v 2>&1 | grep genisoimage, \
	xorrisofs -v 2>&1 | grep xorriso \
))
