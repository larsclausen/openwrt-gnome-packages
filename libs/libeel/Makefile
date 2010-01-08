include $(TOPDIR)/rules.mk

PKG_NAME:=eel
PKG_VERSION:=2.24.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include
EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libeel
  SECTION:=xorg-framework
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libeel
  URL:=http://libeel.sourceforge.net/
  DEPENDS:=+libgconf +gtk2 +glib2 +libglade +libgnome +libgnomeui \
  +libgnome-desktop +libxml2 +libstartup-notification
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{include/eel-2/eel,lib/pkgconfig}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/eel-2/eel/* \
		$(1)/usr/include/eel-2/eel/

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libeel-2.{so*,a,la} \
		$(1)/usr/lib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/libeel/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libeel-2.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libeel))


