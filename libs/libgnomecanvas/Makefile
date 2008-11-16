include $(TOPDIR)/rules.mk

PKG_NAME:=libgnomecanvas
PKG_VERSION:=2.20.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.20
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libgnomecanvas
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnomecanvas
  URL:=http://www.jamesh.id.au/software/libgnomecanvas/
  DEPENDS:=+gtk2 +libart +pango +libglade
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-esd \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libgnomecanvas-2.0/libgnomecanvas}

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomecanvas-2.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomecanvas-2.0/libgnomecanvas/*.h \
		$(1)/usr/include/libgnomecanvas-2.0/libgnomecanvas/
endef

define Package/libgnomecanvas/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomecanvas-2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/libglade/2.0
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libglade/2.0/*.so \
		$(1)/usr/lib/libglade/2.0/
endef

$(eval $(call BuildPackage,libgnomecanvas))


