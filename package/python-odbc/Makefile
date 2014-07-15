#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pyodbc
PKG_VERSION:=3.0.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://pyodbc.googlecode.com/files/
PKG_MD5SUM:=0e47254b17cf563f34852be644826459

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

PKG_BUILD_DEPENDS:=python unixodbc

# TARGET_LDFLAGS += \
# 	-Wl,-rpath=$(STAGING_DIR)/usr/lib

define Package/python-odbc
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python bindings for ODBC
  URL:=https://code.google.com/p/pyodbc/
  DEPENDS:=+python-mini +unixodbc +libstdcpp
endef

define Package/python-odbc/description
  Python bindings for ODBC.
endef

define Build/Compile
  $(call Build/Compile/PyMod,., \
    install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
  )
endef

define Package/python-odbc/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/*.so \
		$(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,python-odbc))
