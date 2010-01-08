#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=empathy
PKG_VERSION:=2.24.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
PKG_MD5SUM:=
PKG_BUILD_DEPENDS:=gnome-doc-utils
PKG_INSTALL=1

include $(INCLUDE_DIR)/package.mk


TARGET_CFLAGS+= \
	-I$(STAGING_DIR)/usr/lib/libintl/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib

define Package/libempathy
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libempathy
  DEPENDS:=+glib2 +libxml2 +libtelepathy-glib +libmission-control
endef

define Package/libempathy-gtk
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libempathy
  DEPENDS:=+glib2 +libempathy +gtk2 +libglade +libgconf +libmission-control \
  +libtelepathy-glib
endef

define Package/empathy
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=empathy
  DEPENDS:=+libdbus-glib +glib2 +libebook +libempathy +gtk2 +libglade \
  +libempathy-gtk +libmission-control +libtelepathy-glib
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-spell \
		--disable-megaphone \
		--disable-nothere \
		--disable-tests \
		--disable-python \
	)
endef

define Package/libempathy/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libempathy.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/share/empathy
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/empathy/{irc-networks.xml,empathy-chatroom-manager.dtd,empathy-irc-networks.dtd,empathy-log-manager.xsl} \
		$(1)/usr/share/empathy/

	$(INSTALL_DIR) $(1)/usr/share/mission-control/profiles
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/mission-control/profiles/* \
		$(1)/usr/share/mission-control/profiles/
endef

define Package/libempathy-gtk/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libempathy-gtk.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/share/empathy
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/empathy/*.glade \
		$(PKG_INSTALL_DIR)/usr/share/empathy/empathy-{contact-groups,status-presets}.dtd \
		$(1)/usr/share/empathy/

	$(INSTALL_DIR) $(1)/usr/share/empathy/icons
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/empathy/icons/* \
		$(1)/usr/share/empathy/icons/

	$(INSTALL_DIR) $(1)/usr/share/icons
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/icons/* \
		$(1)/usr/share/icons/
endef

define Package/empathy/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/empathy \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications
endef

$(eval $(call BuildPackage,libempathy))
$(eval $(call BuildPackage,libempathy-gtk))
$(eval $(call BuildPackage,empathy))
