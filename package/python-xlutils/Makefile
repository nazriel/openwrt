#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xlutils
PKG_VERSION:=1.7.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/x/xlutils/
PKG_MD5SUM:=6247ccda7d8f864b815525e94da30977

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-xlutils
	SECTION:=language-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=xlutils
	URL:=http://www.python-excel.org
	DEPENDS:=+python-mini +python-xlrd +python-xlwt
endef

define Build/Configure
endef

define Build/Compile
	$(INSTALL_DIR) $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlutils
	$(CP) \
		$(PKG_BUILD_DIR)/xlutils/*.py \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlutils
endef

define Package/python-xlutils/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/xlutils \
		$(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,python-xlutils))
