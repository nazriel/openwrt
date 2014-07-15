#
# Copyright (C) 2009-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nilfs-utils
PKG_VERSION:=2.2.0
PKG_MD5SUM:=57480da0c9e6c35100e157b6cc87b6f8
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://nilfs.sourceforge.net/download/

PKG_INSTALL:=1

#PKG_BUILD_DEPENDS:=util-linux liblzo zlib

include $(INCLUDE_DIR)/package.mk

define Package/nilfs-utils
  TITLE:=Utilities for the NILFS2 filsystem
  SECTION:=utils
  CATEGORY:=Utilities
  URL:=http://nilfs.sourceforge.net
  #DEPENDS:=@NAND_SUPPORT
  DEPENDS:=+librt +libuuid +libblkid
endef

define Package/nilfs-utils/description
  Utilities for manipulating NILFS2 file systems.
endef

CONFIGURE_ARGS += \
	--without-selinux

MAKE_FLAGS += \
	DESTDIR="$(PKG_INSTALL_DIR)" \
	BUILDDIR="$(PKG_BUILD_DIR)" \
	#LDLIBS+="$(LIBGCC_S)" \
	#WITHOUT_XATTR=1 \
	#WITHOUT_LZO=1

define Build/Prepare
	$(call Build/Prepare/Default)
	#$(CP) $(SCRIPT_DIR)/config.{guess,sub} $(PKG_BUILD_DIR)/config/
endef

define Package/nilfs-utils/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnilfs{,gc,cleaner}.so.* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/sbin/{mkfs.nilfs2,mount.nilfs2,nilfs-clean,nilfs_cleanerd,nilfs-resize,nilfs-tune,umount.nilfs2} $(1)/sbin/
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/{chcp,dumpseg,lscp,lssu,mkcp,rmcp} $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/etc/nilfs_cleanerd.conf $(1)/etc/
endef

$(eval $(call BuildPackage,nilfs-utils))
