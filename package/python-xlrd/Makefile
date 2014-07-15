#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xlrd
PKG_VERSION:=0.9.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/x/xlrd/
PKG_MD5SUM:=6f3325132f246594988171bc72e1a385

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-xlrd
	SECTION:=language-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=xlrd
	URL:=http://www.python-excel.org
	DEPENDS:=+python-mini
endef

define Build/Configure
endef

define Build/Compile
	$(INSTALL_DIR) $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_BUILD_DIR)/xlrd \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)
endef

define Package/python-xlrd/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlrd \
		$(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,python-xlrd))
