include $(TOPDIR)/rules.mk

PKG_NAME:=gtk-vnc
PKG_VERSION:=0.3.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libgtk-vnc
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgtk-vnc
  URL:=http://www.jamesh.id.au/software/libgtk-vnc/
  DEPENDS:=+gtk2 +libgnutls
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/gtk-vnc-1.0/libgtk-vnc}

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgtk-vnc-1.0.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/gtk-vnc-1.0/*.h \
		$(1)/usr/include/gtk-vnc-1.0/
endef

define Package/libgtk-vnc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgtk-vnc-1.0.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libgtk-vnc))


