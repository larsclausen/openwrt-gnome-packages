include $(TOPDIR)/rules.mk

PKG_NAME:=libgtop
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

define Package/libgtop
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgtop
  URL:=http://www.jamesh.id.au/software/libgtop/
  DEPENDS:=+glib2
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libgtop-2.0/glibtop}

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgtop-2.0.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgtop-2.0/glibtop/*.h \
		$(1)/usr/include/libgtop-2.0/glibtop/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgtop-2.0/*.h \
		$(1)/usr/include/libgtop-2.0/
endef

define Package/libgtop/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgtop-2.0.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libgtop))


