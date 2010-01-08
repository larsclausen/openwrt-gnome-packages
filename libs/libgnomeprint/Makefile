include $(TOPDIR)/rules.mk

PKG_NAME:=libgnomeprint
PKG_VERSION:=2.18.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.18
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libgnomeprint
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnomeprint
  URL:=http://www.jamesh.id.au/software/libgnomeprint/
  DEPENDS:=+glib2 +libart +pango +libxml2 +fontconfig +libfreetype \
           +libgnomecups
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprint-2-2.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/libgnomeprint-2.2/libgnomeprint/private
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomeprint-2.2/libgnomeprint/*.h \
		$(1)/usr/include/libgnomeprint-2.2/libgnomeprint/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomeprint-2.2/libgnomeprint/private/*.h \
		$(1)/usr/include/libgnomeprint-2.2/libgnomeprint/private/
endef

define Package/libgnomeprint/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprint-2-2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/libgnomeprint/2.18.5/modules/{transports,filters}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprint/2.18.5/modules/*.so \
		$(1)/usr/lib/libgnomeprint/2.18.5/modules/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprint/2.18.5/modules/transports/*.so \
		$(1)/usr/lib/libgnomeprint/2.18.5/modules/transports/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprint/2.18.5/modules/filters/*.so \
		$(1)/usr/lib/libgnomeprint/2.18.5/modules/filters/

	$(INSTALL_DIR) $(1)/usr/share/libgnomeprint
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/libgnomeprint/* \
		$(1)/usr/share/libgnomeprint/
endef

$(eval $(call BuildPackage,libgnomeprint))


