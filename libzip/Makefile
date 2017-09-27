#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libzip
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://nih.at/libzip/
PKG_MD5SUM:=8921860aa46437b6a017928f694014b9

include $(INCLUDE_DIR)/package.mk

define Package/libzip/Default
  SECTION:=stethoscope
  CATEGORY:=Stethoscope
  URL:=https://nih.at/libzip/
endef

define Package/libzip
  $(call Package/libzip/Default)
  SUBMENU:=File compress/decompress
  DEPENDS:=+zlib +bzip2
  TITLE:=A File compress/decompress utility
endef

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		CC="$(TARGET_CC)" \
		install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/zip.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libzip/include/zipconf.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib
endef

define Package/libzip/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,libzip))
