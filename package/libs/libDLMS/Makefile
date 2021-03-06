#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libDLMS
PKG_VERSION:=20200612
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_HASH:=
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/Gurux/Gurux.DLMS.cpp.git
PKG_SOURCE_VERSION:=a1f718510fc715268664ca9e56790e265b92a57c

PKG_LICENSE:=GPL
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/libDLMS
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+USE_GLIBC:librt +libstdcpp +libpthread
  TITLE:=A DLMS protocol stack
  URL:=http://gurux.fi/
  ABI_VERSION:=1
endef

define Package/libDLMS/description
 An open-source DLMS protocol stack.
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CROSS)gcc" \
		CXX="$(TARGET_CROSS)g++"
	mkdir -p $(PKG_INSTALL_DIR)/usr/include/dlms/include
	$(CP) $(PKG_BUILD_DIR)/development/include/* $(PKG_INSTALL_DIR)/usr/include/dlms/include
	mkdir -p $(PKG_INSTALL_DIR)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/*.so $(PKG_INSTALL_DIR)/usr/lib/
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include/dlms/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/dlms/include/* $(1)/usr/include/dlms/include
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so $(1)/usr/lib/
endef

define Package/libDLMS/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libDLMS))

