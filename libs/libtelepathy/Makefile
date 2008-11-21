include $(TOPDIR)/rules.mk

PKG_NAME:=libtelepathy
PKG_VERSION:=0.3.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://telepathy.freedesktop.org/releases/$(PKG_NAME)
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

define Package/libtelepathy
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libtelepathy
  URL:=http://www.jamesh.id.au/software/libtelepathy/
  DEPENDS:=+libtelepathy-glib +dbus +libdbus-glib +glib2
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/telepathy-1.0/libtelepathy}

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libtelepathy.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/telepathy-1.0/libtelepathy/*.h \
		$(1)/usr/include/telepathy-1.0/libtelepathy/
endef

define Package/libtelepathy/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libtelepathy.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtelepathy))
