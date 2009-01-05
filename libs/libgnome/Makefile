include $(TOPDIR)/rules.mk

PKG_NAME:=libgnome
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

define Package/libgnome
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnome
  URL:=http://www.jamesh.id.au/software/libgnome/
  DEPENDS:=+glib2 +gnome-vfs +libgconf2 +libbonobo
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-esd \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libgnome-2.0/libgnome}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnome-2.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnome-2.0/libgnome/*.h \
		$(1)/usr/include/libgnome-2.0/libgnome/
endef

define Package/libgnome/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/gnome-open \
		$(1)/usr/bin

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnome-2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/bonobo/{monikers,servers}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/bonobo/monikers/*.so \
		$(1)/usr/lib/bonobo/monikers/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/bonobo/servers/* \
		$(1)/usr/lib/bonobo/servers/

	$(INSTALL_DIR) $(1)/etc/{gconf/schemas,sound/events}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/gconf/schemas/* \
		$(1)/etc/gconf/schemas/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/sound/events/* \
		$(1)/etc/sound/events/

	$(INSTALL_DIR) $(1)/usr/share/gnome-background-properties
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gnome-background-properties/* \
		$(1)/usr/share/gnome-background-properties/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps/backgrounds/gnome
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/backgrounds/gnome/* \
		$(1)/usr/share/pixmaps/backgrounds/gnome/
endef

$(eval $(call BuildPackage,libgnome))
