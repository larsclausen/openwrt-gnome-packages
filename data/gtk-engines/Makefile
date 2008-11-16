#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=gtk-engines
PKG_VERSION:=2.16.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.16
PKG_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

define Package/gtk-engines
  SECTION:=xorg-data
  CATEGORY:=Xorg
  SUBMENU:=data
  TITLE:=gtk-engines
  DEPENDS:=+gtk2
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/gtk-engines/install
	$(INSTALL_DIR) $(1)/usr/lib/gtk-2.0/2.10.0/engines
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/gtk-2.0/2.10.0/engines/*.so \
		$(1)/usr/lib/gtk-2.0/2.10.0/engines/

	$(INSTALL_DIR) $(1)/usr/share/gtk-engines
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gtk-engines/* \
		$(1)/usr/share/gtk-engines/

	$(INSTALL_DIR) $(1)/usr/share/themes/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/themes/* \
		$(1)/usr/share/themes/
endef

$(eval $(call BuildPackage,gtk-engines))
