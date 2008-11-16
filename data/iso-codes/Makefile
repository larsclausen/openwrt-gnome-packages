#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=iso-codes
PKG_VERSION:=3.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=ftp://pkg-isocodes.alioth.debian.org/pub/pkg-isocodes/
PKG_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

define Package/iso-codes
  SECTION:=xorg-data
  CATEGORY:=Xorg
  SUBMENU:=data
  URL:=http://pkg-isocodes.alioth.debian.org/
  TITLE:=iso-codes
  DEPENDS:=
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/iso-codes/install
	$(INSTALL_DIR) $(1)/usr/share/xml/iso-codes
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/xml/iso-codes/* \
		$(1)/usr/share/xml/iso-codes/

	$(INSTALL_DIR) $(1)/usr/share/iso-codes
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/iso-codes/* \
		$(1)/usr/share/iso-codes/
endef

$(eval $(call BuildPackage,iso-codes))
