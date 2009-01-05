#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=gnome-panel
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

define Package/gnome-panel
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=gnome-panel
  DEPENDS:=+libgnome-menu +libgnome-desktop +libgweather +orbit2 +pango +gtk2 \
  +libdbus-glib +libglade +libgconf2 +libbonoboui +libwnck
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-eds \
		--disable-polkit \
		--disable-network-manager \
	)
endef

define Package/gnome-panel/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/bonobo/servers
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/bonobo/servers/* \
		$(1)/usr/lib/bonobo/servers/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/gnome-panel \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/icons/hicolor/48x48/apps
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/icons/hicolor/48x48/apps/* \
		$(1)/usr/share/icons/hicolor/48x48/apps/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications

	$(INSTALL_DIR) $(1)/usr/share/gnome-2.0/ui
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gnome-2.0/ui/* \
		$(1)/usr/share/gnome-2.0/ui/

	$(INSTALL_DIR) $(1)/usr/share/gnome-panel/{glade,pixmaps}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gnome-panel/glade/* \
		$(1)/usr/share/gnome-panel/glade/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gnome-panel/pixmaps/* \
		$(1)/usr/share/gnome-panel/pixmaps/
endef

$(eval $(call BuildPackage,gnome-panel))
