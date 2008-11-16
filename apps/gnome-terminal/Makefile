#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=gnome-terminal
PKG_VERSION:=2.24.1
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

define Package/gnome-terminal
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=gnome-terminal
  DEPENDS:=+glib2 +libgconf2 +gtk2 +libgnomeui +libgnome +vte \
  +libstartup-notification
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Package/gnome-terminal/install
	$(INSTALL_DIR) $(1)/usr/lib/bonobo/servers
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/bonobo/servers/* \
		$(1)/usr/lib/bonobo/servers/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/gnome-terminal
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gnome-terminal/* \
		$(1)/usr/share/gnome-terminal/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications
endef

$(eval $(call BuildPackage,gnome-terminal))
