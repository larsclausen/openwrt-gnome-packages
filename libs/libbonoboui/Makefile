include $(TOPDIR)/rules.mk

PKG_NAME:=libbonoboui
PKG_VERSION:=2.24.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
#PKG_MD5SUM:=d7fb9eb41e8196f1aacf2f08375ae555
PKG_FIXUP:=libtool
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
			  -I$(STAGING_DIR)/usr/libiconv/include
EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
			   -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libbonoboui
  SECTION:=xorg-framework
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libbonoboui
  URL:=http://libbonoboui.sourceforge.net/
  DEPENDS:=+libgnomecanvas +libbonobo +libgnome +libxml2 +libgconf2 +gtk2 \
  +glib2 +libpopt
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{include/libbonoboui-2.0/bonobo,lib/pkgconfig}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libbonoboui-2.0/*.h \
		$(1)/usr/include/libbonoboui-2.0/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libbonoboui-2.0/bonobo/*.h \
		$(1)/usr/include/libbonoboui-2.0/bonobo/

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} \
		$(1)/usr/lib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/libbonoboui/install
	$(INSTALL_DIR) $(1)/usr/lib/libglade/2.0
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libglade/2.0/*.so* \
		$(1)/usr/lib/libglade/2.0/
endef

$(eval $(call BuildPackage,libbonoboui))


