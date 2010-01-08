include $(TOPDIR)/rules.mk

PKG_NAME:=gnome-desktop
PKG_VERSION:=2.24.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
PKG_MD5SUM:=
PKG_FIXUP:=libtool
PKG_BUILD_DEPENDS:=gnome-doc-utils

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libgnome-desktop
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnome-desktop
  URL:=http://www.jamesh.id.au/software/libgnome-desktop/
  DEPENDS:=+libX11 +libXrandr +glib2 +gtk2 +libxml2 +libgnomeui +libgconf2
endef

define Package/gnome-about
  SECTION:=xorg-apps
  CATEGORY:=Xorg
  SUBMENU:=apps
  TITLE:=gnome-about
  URL:=http://www.jamesh.id.au/software/libgnome-desktop/
  DEPENDS:=+glib2 +gnome-vfs +libgconf2 +libbonobo
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-esd \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnome-desktop-2.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/gnome-desktop-2.0/libgnome{,ui}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/gnome-desktop-2.0/libgnome/*.h \
		$(1)/usr/include/gnome-desktop-2.0/libgnome/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/gnome-desktop-2.0/libgnomeui/*.h \
		$(1)/usr/include/gnome-desktop-2.0/libgnomeui/
endef

define Package/libgnome-desktop/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnome-desktop-2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/* \
		$(1)/usr/share/pixmaps/
endef

define Package/gnome-about/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/gnome-about \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/share/applications/gnome-about.desktop \
		$(1)/usr/share/applications/

	$(INSTALL_DIR) $(1)/usr/share/gnome-about
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/gnome-about/* \
		$(1)/usr/share/gnome-about/
endef

$(eval $(call BuildPackage,libgnome-desktop))
$(eval $(call BuildPackage,gnome-about))
