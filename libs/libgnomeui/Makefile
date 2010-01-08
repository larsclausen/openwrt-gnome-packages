include $(TOPDIR)/rules.mk

PKG_NAME:=libgnomeui
PKG_VERSION:=2.24.0
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

define Package/libgnomeui
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnomeui
  URL:=http://www.jamesh.id.au/software/libgnomeui/
  DEPENDS:=+glib2 +libX11 +libSM +libICE +libxml2 +libgnome +gnome-vfs \
  +libgnomecanvas +libbonoboui +libgnome-keyring +libglade
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libgnomeui-2.0/libgnomeui}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeui-2.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomeui-2.0/libgnomeui/*.h \
		$(1)/usr/include/libgnomeui-2.0/libgnomeui/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomeui-2.0/*.h \
		$(1)/usr/include/libgnomeui-2.0/
endef

define Package/libgnomeui/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeui-2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/libglade/2.0
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libglade/2.0/*.so \
		$(1)/usr/lib/libglade/2.0/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/* \
		$(1)/usr/share/pixmaps/
endef

$(eval $(call BuildPackage,libgnomeui))


