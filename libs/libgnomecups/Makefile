include $(TOPDIR)/rules.mk

PKG_NAME:=libgnomecups
PKG_VERSION:=0.2.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/0.2
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/

define Package/libgnomecups
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnomecups
  URL:=http://www.jamesh.id.au/software/libgnomecups/
  DEPENDS:=+glib2 +cups
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libgnomecups-1/libgnomecups}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomecups-1.0.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomecups-1/libgnomecups/*.h \
		$(1)/usr/include/libgnomecups-1/libgnomecups/
endef

define Package/libgnomecups/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomecups-1.0.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libgnomecups))
