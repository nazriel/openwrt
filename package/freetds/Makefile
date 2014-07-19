#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=freetds
PKG_VERSION:=0.92.405
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=ftp://ftp.freetds.org/pub/freetds/stable/
PKG_MD5SUM:=51e9210358fd03a720597b4dc762fe67

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
#include $(INCLUDE_DIR)/nls.mk

# TARGET_LDFLAGS += \
# 	-Wl,-rpath=$(STAGING_DIR)/usr/lib

define Package/freetds/Default
  SUBMENU:=database
  TITLE:=FreeTDS
  URL:=http://www.freetds.org
endef

define Package/freetds
  $(call Package/freetds/Default)
  TITLE+=
  SECTION:=libs
  CATEGORY:=Libraries
endef

define Package/freetds/description
  FreeTDS common files.
endef

define Package/freetds-libs
  $(call Package/freetds/Default)
  TITLE+= (libraries)
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+freetds
endef

define Package/freetds-libs/description
  FreeTDS standalone libraries.
endef

define Package/freetds-odbc
  $(call Package/freetds/Default)
  TITLE+= (odbc driver)
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+unixodbc +freetds
endef

define Package/freetds-odbc/description
  FreeTDS driver for unixODBC.
endef

define Package/freetds-utils
  $(call Package/freetds/Default)
  TITLE+= (utilities)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+freetds-libs
endef

define Package/freetds-utils/description
  FreeTDS command line utilities.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR="$(PKG_INSTALL_DIR)" install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/etc
	$(CP) $(PKG_INSTALL_DIR)/etc/*.conf $(1)/etc
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include
endef

define Package/freetds/install
	$(INSTALL_DIR) $(1)/etc
	$(CP) $(PKG_INSTALL_DIR)/etc/*.conf $(1)/etc
endef

define Package/freetds-libs/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{ct,sybdb}.*so* $(1)/usr/lib
endef

define Package/freetds-odbc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtdsodbc.*so* $(1)/usr/lib
endef

define Package/freetds-utils/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
endef

$(eval $(call BuildPackage,freetds))
$(eval $(call BuildPackage,freetds-libs))
$(eval $(call BuildPackage,freetds-odbc))
$(eval $(call BuildPackage,freetds-utils))
