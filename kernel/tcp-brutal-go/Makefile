include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=tcp-brutal-go
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_URL:=https://github.com/phuslu/tcp-brutal
PKG_SOURCE_URL:=$(PKG_URL).git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_DATE:=2026-05-1
PKG_MIRROR_HASH:=18f4e386f6f703f183595e94aeef3a348102a9d884c9e646aa3aee1671c75784
PKG_LICENSE:=GPL-3.0

PKG_MAINTAINER:=Haruue Icymoon <i@haruue.moe>

include $(INCLUDE_DIR)/package.mk

define KernelPackage/brutal-go
	SECTION:=kernel
	SUBMENU:=Network Support
	TITLE:=TCP Brutal Go Kernel module
	FILES:=$(PKG_BUILD_DIR)/brutal-go.$(LINUX_KMOD_SUFFIX)
	AUTOLOAD:=$(call AutoLoad,30,brutal-go)
endef

define KernelPackage/brutal-go/description
	Hysteria's congestion control algorithm ported to kernel mode TCP
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define Build/Configure
endef

define Build/Compile
	$(KERNEL_MAKE) M="$(PKG_BUILD_DIR)" modules
endef

$(eval $(call KernelPackage,brutal-go))
