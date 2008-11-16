include $(TOPDIR)/rules.mk

PKG_NAME:=totem-pl-parser
PKG_VERSION:=2.24.2
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

define Package/libtotem-plparser
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libtotem-pl-parser
  URL:=http://www.jamesh.id.au/software/libtotem-pl-parser/
  DEPENDS:=+glib2 +gtk2 +libxml2
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--without-hal \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/totem-pl-parser/1/plparser}

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libtotem-plparser{,-mini}.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/totem-pl-parser/1/plparser/*.h \
		$(1)/usr/include/totem-pl-parser/1/plparser/
endef

define Package/libtotem-plparser/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libtotem-plparser{,-mini}.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtotem-plparser))


