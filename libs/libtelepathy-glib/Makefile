include $(TOPDIR)/rules.mk

PKG_NAME:=telepathy-glib
PKG_VERSION:=0.7.18
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://telepathy.freedesktop.org/releases/$(PKG_NAME)
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

define Package/libtelepathy-glib
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libtelepathy-glib
  URL:=http://www.jamesh.id.au/software/libtelepathy-glib/
  DEPENDS:=+glib2 +dbus +libdbus-glib
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/telepathy-1.0/telepathy-glib/_gen}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libtelepathy-glib.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/telepathy-1.0/telepathy-glib/*.h \
		$(1)/usr/include/telepathy-1.0/telepathy-glib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/telepathy-1.0/telepathy-glib/_gen/*.h \
		$(1)/usr/include/telepathy-1.0/telepathy-glib/_gen
endef

define Package/libtelepathy-glib/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libtelepathy-glib.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtelepathy-glib))


