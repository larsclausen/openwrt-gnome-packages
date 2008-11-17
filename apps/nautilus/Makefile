#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=nautilus
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

define Package/nautilus
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=nautilus
  DEPENDS:=+libstartup-notification +libeel +glib2 +libgnome-desktop +orbit2 \
  +pango +gtk2 +libbonobo +libgnome +libgnomeui +librsvg +libxml2 +libexif
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-xmp \
		--disable-tracker \
		--disable-beagle \
	)
endef

define Package/nautilus/install
	$(INSTALL_DIR) $(1)/etc/gconf/schemas
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/etc/gconf/schemas/* \
		$(1)/etc/gconf/schemas/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/bonobo/servers
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/bonobo/servers/* \
		$(1)/usr/lib/bonobo/servers/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications

	$(INSTALL_DIR) $(1)/usr/share/pixmaps/nautilus
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/nautilus/* \
		$(1)/usr/share/pixmaps/nautilus/

	$(INSTALL_DIR) $(1)/usr/share/mime
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/mime/* \
		$(1)/usr/share/mime/

	$(INSTALL_DIR) $(1)/usr/share/icons/hicolor
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/icons/hicolor/* \
		$(1)/usr/share/icons/hicolor/

	$(INSTALL_DIR) $(1)/usr/share/nautilus/{glade,patterns,ui}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/nautilus/glade/* \
		$(1)/usr/share/nautilus/glade/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/nautilus/patterns/* \
		$(1)/usr/share/nautilus/patterns/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/nautilus/ui/* \
		$(1)/usr/share/nautilus/ui/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/nautilus/*.{xml,placeholder} \
		$(1)/usr/share/nautilus/
endef

$(eval $(call BuildPackage,nautilus))
