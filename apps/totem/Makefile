#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=totem
PKG_VERSION:=2.24.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
#PKG_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

TARGET_CFLAGS+= \
	-I$(STAGING_DIR)/usr/lib/libintl/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib

define Package/totem
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=totem
  DEPENDS:=+libgnomeui +gst-plugins-base +gst-plugins-good +gnome-icon-theme \
  +libtotem-plparser +iso-codes
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-python \
		--disable-vala \
		--disable-browser-plugins \
		--disable-basic-plugin \
		--disable-gmp-plugin \
		--disable-complex-plugin \
		--disable-narrowspace-plugin \
		--disable-mully-plugin \
		--disable-cone-plugin \
		--disable-nautilus \
		--disable-xine \
		--disable-nvtv \
		--with-plugins=none \
	)
endef

define Package/totem/install
	$(INSTALL_DIR) $(1)/etc/gconf/schemas
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/gconf/schemas/* \
		$(1)/etc/gconf/schemas/

	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/icons/hicolor/48x48/apps
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/icons/hicolor/48x48/apps/* \
		$(1)/usr/share/icons/hicolor/48x48/apps/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications/

	$(INSTALL_DIR) $(1)/usr/share/totem
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/totem/* \
		$(1)/usr/share/totem/
endef

$(eval $(call BuildPackage,totem))
