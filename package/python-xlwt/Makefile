#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xlwt
PKG_VERSION:=0.7.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/x/xlwt/
PKG_MD5SUM:=59cb5efd55319465dfcd25e6a485f03c

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-xlwt
	SECTION:=language-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=xlwt
	URL:=http://www.python-excel.org
	DEPENDS:=+python-mini
endef

define Build/Configure
endef

define Build/Compile
	$(INSTALL_DIR) $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlwt
	$(CP) \
		$(PKG_BUILD_DIR)/xlwt/*.py \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlwt
endef

define Package/python-xlwt/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/xlwt
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlwt/*.py \
		$(1)$(PYTHON_PKG_DIR)/xlwt
endef

$(eval $(call BuildPackage,python-xlwt))
