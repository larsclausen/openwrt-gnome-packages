#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=gedit
PKG_VERSION:=2.24.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
PKG_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

TARGET_CFLAGS+= \
	-I$(STAGING_DIR)/usr/lib/libintl/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib

define Package/gedit
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=gedit
  DEPENDS:=+libxml2 +libSM +glib2 +gtk2 +libgtksourceview +libgconf2
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-spell \
		--disable-python \
		--disable-attr \
	)
endef

define Package/gedit/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/gedit \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications

	$(INSTALL_DIR) $(1)/usr/share/gedit-2/{icons,logo,taglist,ui}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gedit-2/icons/* \
		$(1)/usr/share/gedit-2/icons/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gedit-2/logo/* \
		$(1)/usr/share/gedit-2/logo/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gedit-2/taglist/* \
		$(1)/usr/share/gedit-2/taglist/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gedit-2/ui/* \
		$(1)/usr/share/gedit-2/ui/
endef

$(eval $(call BuildPackage,gedit))
