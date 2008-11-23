include $(TOPDIR)/rules.mk

PKG_NAME:=evolution-data-server
PKG_VERSION:=2.24.1.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.24
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

TARGET_CFLAGS+= \
	-I$(STAGING_DIR)/usr/lib/libintl/include \
	-I$(STAGING_DIR)/usr/lib/libiconv/include

TARGET_LDFLAGS+=\
    -Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib/

define Package/evolution-data-server
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=evolution-data-server
  URL:=http://www.jamesh.id.au/software/evolution-data-server/
  DEPENDS:=+libsqlite3 +glib2 +libgnome +gnome-vfs +libbonobo \
  +libxml2 +libsoup +libcamel +libdb +libebook +libecal +libedata-book \
  +libedata-cal +libedataserver +libegroupwise +libgconf2 +libgdata \
  +libgdata-google +zlib +libxml2 +orbit2 +libpopt
endef

define Package/libgdata
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=Library for
  DEPENDS:=+glib2 +libxml2 +libsoup
endef

define Package/libgdata-google
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=Library for
  DEPENDS:=+libgdata +libgdata
endef

define Package/libcamel
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libcamel
  DEPENDS:=+glib2 +libedataserver +libgconf2 +gnome-vfs +zlib
endef

define Package/libebackend
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libebackend
  DEPENDS:=+glib2
endef

define Package/libebook
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libebook
  DEPENDS:=+glib2 +libxml2 +libedataserver
endef

define Package/libecal
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libecal
  DEPENDS:=+glib2 +libedataserver
endef

define Package/libedata-book
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libedata-book
  DEPENDS:=+glib2 +libbonobo +orbit2 +libedataserver +libebook +libdb \
  +libebackend
endef

define Package/libedata-cal
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libedata-cal
  DEPENDS:=+glib2 +libbonobo +orbit2 +libedataserver +libecal +libebackend
endef

define Package/libedataserver
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libedataserver
  DEPENDS:=+glib2 +libgconf2 +libbonobo +libxml2 +libsoup
endef

define Package/libedataserverui
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libedataserverui
  DEPENDS:=+glib2 +libglade +gtk2 +libebook +libedataserver
endef

define Package/libical
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libical
  DEPENDS:=
endef

define Package/libegroupwise
  SECTION:=libs
  CATEGORY:=libraries
  TITLE:=libgroupwise
  DEPENDS:=+glib2 +libxml2 +libsoup
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--libexecdir=/usr/lib/evolution-data-server \
		--with-libiconv=$(STAGING_DIR)/usr/lib/libiconv \
		--with-libdb=$(STAGING_DIR)/usr/ \
        --disable-nss \
        --disable-smime \
        --disable-gnome-keyring \
        --disable-ipv6 \
        --enable-calendar \
        --enable-nntp \
        --disable-imapp \
        --disable-imap4 \
        --disable-hula \
        --enable-dot-locking \
        --enable-largefile \
        --disable-glibtest \
		, \
		ac_cv_libiconv=yes \
		ac_cv_libiconv_utf8=yes \
	)
	$(CP) ./files/iconv-detect.h $(PKG_BUILD_DIR)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/evolution-data-server-2.24
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/evolution-data-server-2.24/* \
		$(1)/usr/include/evolution-data-server-2.24/
endef

define Package/evolution-data-server/install
	$(INSTALL_DIR) $(1)/usr/lib/evolution-data-server-1.2/camel-providers
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/evolution-data-server-1.2/camel-providers/*.so* \
		$(1)/usr/lib/evolution-data-server-1.2/camel-providers

	$(INSTALL_DIR) $(1)/usr/lib/evolution-data-server-1.2/extensions
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/evolution-data-server-1.2/extensions/*.so* \
		$(1)/usr/lib/evolution-data-server-1.2/extensions

	$(INSTALL_DIR) $(1)/usr/lib/bonobo/servers
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/bonobo/servers/* \
		$(1)/usr/lib/bonobo/servers/

	$(INSTALL_DIR) $(1)/usr/lib/evolution-data-server
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/evolution-data-server/* \
		$(1)/usr/lib/evolution-data-server/

	$(INSTALL_DIR) $(1)/usr/share/evolution-data-server-2.24/{glade,weather}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/evolution-data-server-2.24/glade/* \
		$(1)/usr/share/evolution-data-server-2.24/glade/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/evolution-data-server-2.24/weather/* \
		$(1)/usr/share/evolution-data-server-2.24/weather/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps/evolution-data-server
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/evolution-data-server/* \
		$(1)/usr/share/pixmaps/evolution-data-server/
endef

define Package/evolution-data-server/install/Default
	$(INSTALL_DIR) $(2)/usr/lib
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/$(1).so* \
		$(2)/usr/lib
endef

define Package/libcamel/install
$(call Package/evolution-data-server/install/Default,libcamel{$(comma)-provider}-1.2,$(1))
endef

define Package/libebackend/install
$(call Package/evolution-data-server/install/Default,libebackend-1.2,$(1))
endef

define Package/libebook/install
$(call Package/evolution-data-server/install/Default,libebook-1.2,$(1))
endef

define Package/libecal/install
$(call Package/evolution-data-server/install/Default,libecal-1.2,$(1))
endef

define Package/libedata-book/install
$(call Package/evolution-data-server/install/Default,libedata-book-1.2,$(1))
endef

define Package/libedata-cal/install
$(call Package/evolution-data-server/install/Default,libedata-cal-1.2,$(1))
endef

define Package/libedataserver/install
$(call Package/evolution-data-server/install/Default,libedataserver-1.2,$(1))
endef

define Package/libedataserverui/install
$(call Package/evolution-data-server/install/Default,libedataserverui-1.2,$(1))
endef

define Package/libegroupwise/install
$(call Package/evolution-data-server/install/Default,libegroupwise-1.2,$(1))
endef

define Package/libgdata/install
$(call Package/evolution-data-server/install/Default,libgdata-1.2,$(1))
endef

define Package/libgdata-google/install
$(call Package/evolution-data-server/install/Default,libgdata-google-1.2,$(1))
endef

$(eval $(call BuildPackage,evolution-data-server))
$(eval $(call BuildPackage,libcamel))
$(eval $(call BuildPackage,libebackend))
$(eval $(call BuildPackage,libebook))
$(eval $(call BuildPackage,libecal))
$(eval $(call BuildPackage,libedata-book))
$(eval $(call BuildPackage,libedata-cal))
$(eval $(call BuildPackage,libedataserver))
$(eval $(call BuildPackage,libedataserverui))
$(eval $(call BuildPackage,libegroupwise))
$(eval $(call BuildPackage,libgdata))
$(eval $(call BuildPackage,libgdata-google))


