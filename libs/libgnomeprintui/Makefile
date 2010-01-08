include $(TOPDIR)/rules.mk

PKG_NAME:=libgnomeprintui
PKG_VERSION:=2.18.3
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

define Package/libgnomeprintui
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libgnomeprintui
  URL:=http://www.jamesh.id.au/software/libgnomeprintui/
  DEPENDS:=+gtk2 +libgnomeprint +libgnomecanvas +gnome-icon-theme +libglade
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprintui-2-2.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/libgnomeprintui-2.2/libgnomeprintui
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libgnomeprintui-2.2/libgnomeprintui/*.h \
		$(1)/usr/include/libgnomeprintui-2.2/libgnomeprintui/
endef

define Package/libgnomeprintui/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libgnomeprintui-2-2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/share/libgnomeprintui/2.18.3
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/libgnomeprintui/2.18.3/* \
		$(1)/usr/share/libgnomeprintui/2.18.3/
endef

$(eval $(call BuildPackage,libgnomeprintui))
