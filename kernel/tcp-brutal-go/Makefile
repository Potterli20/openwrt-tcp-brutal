include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=tcp-brutal-go
PKG_VERSION:=1.0.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/phuslu/tcp-brutal/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=41b89ff9c06c87da0c62f6ea54c17cb8a24a14b713522a2101dc6f292c4f0412
PKG_LICENSE:=GPL-3.0

PKG_MAINTAINER:=phuslu

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

define Build/Prepare
	$(call Build/Prepare/Default)
	$(CP) ./files/Makefile $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef

define Build/Compile
	$(KERNEL_MAKE) M="$(PKG_BUILD_DIR)" modules
endef

$(eval $(call KernelPackage,brutal-go))
