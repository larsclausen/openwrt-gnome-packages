include $(TOPDIR)/rules.mk

PKG_NAME:=gtksourceview
PKG_VERSION:=2.4.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.4
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libgtksourceview
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgtksourceview
  URL:=http://www.jamesh.id.au/software/libgtksourceview/
  DEPENDS:=+glib2 +gtk2 +libxml2
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/gtksourceview-2.0/gtksourceview}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgtksourceview-2.0.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/gtksourceview-2.0/gtksourceview/*.h \
		$(1)/usr/include/gtksourceview-2.0/gtksourceview/
endef

define Package/libgtksourceview/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgtksourceview-2.0.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/share/gtksourceview-2.0/{language-specs,styles}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gtksourceview-2.0/language-specs/* \
		$(1)/usr/share/gtksourceview-2.0/language-specs/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/gtksourceview-2.0/styles/* \
		$(1)/usr/share/gtksourceview-2.0/styles/
endef

$(eval $(call BuildPackage,libgtksourceview))


