include $(TOPDIR)/rules.mk

PKG_NAME:=libgweather
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

define Package/libgweather
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgweather
  URL:=http://www.jamesh.id.au/software/libgweather/
  DEPENDS:=+glib2 +gnome-vfs +libgconf2 +libbonobo
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libgweather}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgweather.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgweather/*.h \
		$(1)/usr/include/libgweather/
endef

define Package/libgweather/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgweather.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/etc/gconf/schemas
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/gconf/schemas/* \
		$(1)/etc/gconf/schemas/

	$(INSTALL_DIR) $(1)/usr/share/libgweather
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/libgweather/* \
		$(1)/usr/share/libgweather/
endef

$(eval $(call BuildPackage,libgweather))
