include $(TOPDIR)/rules.mk

PKG_NAME:=libjsoncpp
PKG_VERSION:=0.18.3
PKG_REV:=2de18021fcb11370e9b5a1fbe7dcfd673533a134

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/open-source-parsers/jsoncpp.git

PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_REV).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

CMAKE_OPTIONS:=-DJSONCPP_WITH_TESTS=OFF -DBUILD_SHARED_LIBS=ON -DBUILD_STATIC_LIBS=OFF

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libjsoncpp
	SECTION:=stethoscope
	CATEGORY:=Stethoscope
	TITLE:=implementation of a JSON reader and writer in C++
	DEPENDS:=+libstdcpp
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/json
	$(CP) $(PKG_INSTALL_DIR)/usr/include/json/* $(1)/usr/include/json/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib
endef

define Package/libjsoncpp/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,libjsoncpp))
