include $(TOPDIR)/rules.mk

PKG_NAME:=aws-sdk-cpp
PKG_VERSION:=1.2.1
PKG_REV:=0cbe1123a0da7a4a77a5ba359d767321931747e2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/BennyWang/aws-sdk-cpp.git

PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_REV).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_OPTIONS:=-DBUILD_ONLY="core;kinesis" -DENABLE_TESTING=OFF

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/aws-sdk-cpp
	SECTION:=stethoscope
	CATEGORY:=Stethoscope
	TITLE:=aws sdk in C++
	DEPENDS:=+libcurl +libopenssl +zlib +libstdcpp
endef

#sed -i 's/#if OPENSSL_VERSION_LESS_1_1/#if OPENSSL_VERSION_LESS_1_1 \&\& !defined\(OPENSSL_NO_DEPRECATED\)/1' $(PKG_BUILD_DIR)/aws-cpp-sdk-core/source/utils/crypto/openssl/CryptoImpl.cpp
define Build/Configure
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/aws
	$(CP) $(PKG_INSTALL_DIR)/usr/include/aws/core $(1)/usr/include/aws/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/aws/kinesis $(1)/usr/include/aws/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib
endef

define Package/aws-sdk-cpp/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,aws-sdk-cpp))
