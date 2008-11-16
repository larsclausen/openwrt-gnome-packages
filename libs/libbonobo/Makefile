include $(TOPDIR)/rules.mk

PKG_NAME:=libbonobo
PKG_VERSION:=2.24.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
#PKG_MD5SUM:=d7fb9eb41e8196f1aacf2f08375ae555
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
              -I$(STAGING_DIR)/usr/libiconv/include
EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
               -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libbonobo
  SECTION:=xorg-framework
  CATEGORY:=Xorg
  SUBMENU:=lib
  TITLE:=libbonobo
  URL:=http://libbonobo.sourceforge.net/
  DEPENDS:=+libpopt +orbit2
endef

define Build/Configure
	$(call Build/Configure/Default,--disable-threads)
endef

define Build/InstallDev
	$(CP) $(PKG_INSTALL_DIR)/* $(1)
endef

define Package/libbonobo/install
	$(CP) $(PKG_INSTALL_DIR)/* $(1)
endef

$(eval $(call BuildPackage,libbonobo))


