#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=dia
PKG_VERSION:=0.96.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/0.96
PKG_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

TARGET_CFLAGS+= \
	-I$(STAGING_DIR)/usr/lib/libintl/include/ \
	-I$(STAGING_DIR)/usr/lib/libiconv/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib \
	-L$(STAGING_DIR)/usr/lib/libiconv/lib

define Package/dia
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=dia
  DEPENDS:=+gtk2 +glib2 +libxml2 +pango +libart +cairo +libxslt +libpopt
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--without-python \
		--with-cairo \
	)
endef

define Package/dia/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/dia \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/lib/dia
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/dia/*.so \
		$(1)/usr/lib/dia/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications/

	$(INSTALL_DIR) $(1)/usr/share/mime-info
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/mime-info/* \
		$(1)/usr/share/mime-info/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/* \
		$(1)/usr/share/pixmaps/

	$(INSTALL_DIR) $(1)/usr/share/dia/{shapes,sheets,ui,xslt}
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/dia/shapes/* \
		$(1)/usr/share/dia/shapes/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/dia/sheets/* \
		$(1)/usr/share/dia/sheets/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/dia/xslt/* \
		$(1)/usr/share/dia/xslt/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/dia/ui/* \
		$(1)/usr/share/dia/ui/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/dia/dia_logo.png \
		$(1)/usr/share/dia/
endef

$(eval $(call BuildPackage,dia))
