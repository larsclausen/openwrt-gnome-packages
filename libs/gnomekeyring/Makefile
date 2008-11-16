include $(TOPDIR)/rules.mk

PKG_NAME:=gnome-keyring
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

define Package/libgnome-keyring
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=gnome-keyring
  URL:=http://www.jamesh.id.au/software/gnome-keyring/
  DEPENDS:=+libtasn1 +glib2 +gconf2 +libgp11
endef

define Package/libgp11
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=gp11
  URL:=http://www.jamesh.id.au/software/gnome-keyring/
  DEPENDS:=+glib2
endef

define Package/gnome-keyring
  SECTION:=xorg-utils
  CATEGORY:=Xorg
  SUBMENU:=utilities
  TITLE:=gnome-keyring
  URL:=http://www.jamesh.id.au/software/gnome-keyring/
  DEPENDS:=+libgnome-keyring
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--with-libtasn1-prefix=$(STAGING_DIR)/usr \
		, \
		ac_cv_file__dev_random=no \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnome-keyring.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgp11.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/{gnome-keyring-1,gp11}

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/gnome-keyring-1/*.h \
		$(1)/usr/include/gnome-keyring-1/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/gp11/*.h \
		$(1)/usr/include/gp11/
endef

define Package/libgnome-keyring/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnome-keyring.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/gnome-keyring/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/gnome-keyring/*.so \
		$(1)/usr/lib/gnome-keyring/

	$(INSTALL_DIR) $(1)/etc/gconf/schemas
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/gconf/schemas/* \
		$(1)/etc/gconf/schemas/
endef

define Package/libgp11/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgp11.so* \
		$(1)/usr/lib/
endef

define Package/gnome-keyring/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALLD_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/dbus-1/services
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/dbus-1/services/* \
		$(1)/usr/share/dbus-1/services/
endef

$(eval $(call BuildPackage,libgnome-keyring))
$(eval $(call BuildPackage,libgp11))


